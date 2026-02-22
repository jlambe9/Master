# Neo4J Schema Design — v1.3 Goal Framework

> **Version:** 1.0
> **Date:** 2026-02-22
> **Status:** REFERENCE — implement when graph database is provisioned
> **Dependency:** Framework must work markdown-native. This schema is the eventual graph translation.

---

## Design Principles

1. Every markdown section maps to a Neo4J element
2. Files = nodes, properties = properties, links = relationships
3. No redundant properties that duplicate edges (single source of truth)
4. Versioning via `deprecated`/`replacedBy` properties (lightweight, not full temporal model)

---

## Node Types

### Strategy Layer

```cypher
(:Goal {
  id: String,            // "GOAL-001"
  name: String,
  metric: String,        // "£5000/month"
  metricValue: Float,    // 5000
  metricUnit: String,    // "GBP/month"
  measurement: String,   // "Stripe MRR"
  deadline: Date,
  status: String,        // ACTIVE|PAUSED|ACHIEVED|ABANDONED
  mode: String,          // BUILDING|OPERATIONAL
  strategySummary: String,
  created: Date,
  framework: String      // "v1.3"
})

(:SubGoal {
  id: String,            // "SG-001"
  name: String,
  metric: String,
  metricValue: Float,
  currentValue: Float,
  target: Float,
  status: String
})

(:MechanismStep {
  id: String,            // "M1"
  name: String,          // "Outreach"
  inputLabel: String,    // "People contacted"
  outputLabel: String,   // "Conversations started"
  conversionRatio: Float,
  currentThroughput: Float,
  throughputUnit: String, // "per_week"
  isBottleneck: Boolean,
  deprecated: Boolean,    // false by default
  replacedBy: String      // null, or "M2a,M2b" if step was split
})

(:Foundation {
  id: String,            // "FND-OFFER"
  name: String,          // "Offer"
  currentState: String,  // "Google Doc with generic plan"
  maturity: String,      // raw|draft|tested|proven
  sufficient: Boolean
})
```

### Execution Layer

```cypher
(:Path {
  id: String,            // "PATH-LI"
  name: String,          // "LinkedIn Outreach"
  status: String,        // ACTIVE|PAUSED|NOT_STARTED|DROPPED
  isMVP: Boolean,
  created: Date,
  droppedDate: Date,     // null unless DROPPED
  droppedReason: String, // null unless DROPPED
  finalMetrics: String   // null unless DROPPED — summary for Path Archive
})

(:Task { ... })          // Existing v1.2 — no changes to schema
(:Subtask { ... })       // Existing v1.2 — no changes to schema
```

### Cross-Cutting

```cypher
(:ThresholdGate {
  id: String,            // "TG-001"
  condition: String,     // "≥3 clients signed"
  metric: String,
  threshold: Float,
  currentValue: Float,
  source: String,        // Where to read the metric (collapsed from MetricSource node)
  status: String         // LOCKED|UNLOCKED
})
```

**Note:** `MetricSource` is collapsed to a `source` property on `ThresholdGate`. Promote to a separate node type when >10 gates share sources across goals.

---

## Edge Types

### Strategy Hierarchy

```cypher
// Goal owns sub-goals
(:Goal)-[:HAS_SUBGOAL {order: Int}]->(:SubGoal)

// Sub-goal owns mechanism steps (ownership only, NOT ordering)
(:SubGoal)-[:HAS_MECHANISM]->(:MechanismStep)

// Mechanism steps chain to each other (THIS is the ordering)
(:MechanismStep)-[:CHAINS_TO]->(:MechanismStep)
```

**Design decision:** `CHAINS_TO` is the single source of truth for step ordering. `HAS_MECHANISM` has no `order` property — it expresses ownership only. This prevents dual-ordering desync and supports future branching funnels (M2 → M2a, M2b) without schema changes.

### Foundations

```cypher
(:Goal)-[:HAS_FOUNDATION]->(:Foundation)
(:Foundation)-[:IMPLEMENTED_BY]->(:Task)
```

**Uniqueness constraint:** Foundations are identified globally by name. If two goals need "Offer", they both reference the same Foundation node.

```cypher
CREATE CONSTRAINT foundation_name_unique FOR (f:Foundation) REQUIRE f.name IS UNIQUE
```

### Paths → Mechanism Steps

```cypher
(:Path)-[:FEEDS {contribution: Float}]->(:MechanismStep)
```

### Execution

```cypher
(:Path)-[:CONTAINS_TASK {order: Int}]->(:Task)
(:Task)-[:HAS_SUBTASK]->(:Subtask)            // existing v1.2
(:Task)-[:DEPENDS_ON {type: String}]->(:Task)  // existing v1.2
```

### Threshold Gates

```cypher
(:Goal)-[:HAS_GATE]->(:ThresholdGate)
(:ThresholdGate)-[:UNLOCKS {targetType: String}]->(:Task | :Path)
```

**Design decision:** `UNLOCKS` is constrained to `Task | Path` only (not SubGoal). Unlocking a sub-goal should be modelled as a new goal, not a gated sub-goal. The `targetType` property (`'Task'` or `'Path'`) enables efficient filtering.

---

## Key Queries

```cypher
// 1. What foundations are missing?
MATCH (g:Goal {id:'GOAL-001'})-[:HAS_FOUNDATION]->(f:Foundation {sufficient: false})
RETURN f.name, f.currentState

// 2. Current bottleneck
MATCH (g:Goal)-[:HAS_SUBGOAL]->()-[:HAS_MECHANISM]->(m:MechanismStep {isBottleneck: true})
RETURN m.name, m.conversionRatio, m.currentThroughput

// 3. Trace task → goal (≤4 hops)
MATCH (t:Task {id:'LP-003'})<-[:CONTAINS_TASK]-(p:Path)-[:FEEDS]->(m:MechanismStep)
      <-[:HAS_MECHANISM]-(sg:SubGoal)<-[:HAS_SUBGOAL]-(g:Goal)
RETURN t.id, p.name, m.name, sg.name, g.name

// 4. Threshold gates approaching unlock (≥80%)
MATCH (tg:ThresholdGate)
WHERE tg.currentValue >= tg.threshold * 0.8
RETURN tg.condition, tg.currentValue, tg.threshold

// 5. MVP path — what's left?
MATCH (p:Path {isMVP: true})-[:CONTAINS_TASK]->(t:Task)
WHERE t.status <> 'COMPLETED'
RETURN t.id, t.name, t.status ORDER BY t.priority

// 6. All paths feeding the bottleneck
MATCH (p:Path)-[:FEEDS]->(m:MechanismStep {isBottleneck: true})
RETURN p.name, p.status

// 7. Foundations shared across goals
MATCH (f:Foundation)<-[:HAS_FOUNDATION]-(g:Goal)
RETURN f.name, f.sufficient, collect(g.name) as goals

// 8. Deprecated mechanism steps and their replacements
MATCH (m:MechanismStep {deprecated: true})
RETURN m.name, m.replacedBy
```

---

## Sync Rules

1. **Goal markdown file is authoritative.** Sync script reads markdown → upserts Neo4J.
2. **Task `Goal:` field is a convenience mirror.** Sync script validates bidirectional consistency and flags mismatches.
3. **Foundation uniqueness enforced at graph level.** If two goal files reference "Offer", sync creates one node with two `HAS_FOUNDATION` edges.
4. **Dropped paths:** When a path status changes to DROPPED, sync populates `droppedDate`, `droppedReason`, `finalMetrics` from the Path Archive section.
5. **SUBSUMED tasks:** Tasks with status SUBSUMED get a `(:Task)-[:SUBSUMED_BY]->(:Task)` edge. Old node retained for history.

---

## Migration Notes

- No Neo4J database exists yet. This schema is the target for when one is provisioned.
- The sync script specification is a separate deliverable (not part of v1.3 framework).
- All queries above should work unchanged once data is loaded.
- Task schema (v1.2) is unchanged — no migration needed for existing tasks.
