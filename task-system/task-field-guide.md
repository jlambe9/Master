# Task Field Guide — How to Fill Out Task Files

*Reference for any agent creating or updating tasks. Linked from every task template.*
*Source of truth for: owner classification, task levels, field definitions, RTP graduation, maturity.*

## Completion Gate

A task is NOT done until every output in its Win State "Outputs" list verifiably exists. Steps and subtasks each have an "Output (proof of completion)" column — these must also exist.

No vague win states. No self-reporting without verification. If the outputs aren't defined, the task can't be completed — it needs output definitions first.

Full protocol: ~/clawd/AGENTS.md → Step 5: Mark Completion.

## Owner Classification

Owner is NOT permanent. It's a function of how well-defined the task is + whether output can be verified without Jamie. Tasks move 🧑→🔄→🤖 as they mature.

### 🤖 Rich (Bucket 1: Rich E2E)
ALL of these must be true:
- Steps are fully defined (not CAPTURED/GOAL CLARITY)
- Inputs are available (no missing tools/data/access)
- Output is machine-verifiable OR doesn't need human judgment
- No subjective quality gate (e.g. "does this sound right?")

### 🔄 Hybrid (Bucket 2: Rich + Jamie Handoff)
ANY of these:
- Rich can do some steps but Jamie must do others
- Rich produces output but Jamie must review/approve before "done" (e.g. intros — Rich writes, Jamie validates)
- Task has decision points that require Jamie's judgment
- Rich can draft but Jamie makes the final call

### 🧑 Jamie (Bucket 3: Jamie Only)
ANY of these:
- Physical task (clean flat, gym, cooking)
- Requires Jamie's personal presence (Saida conversation, sales call)
- Task is undefined — Jamie's job IS to define it so it can become Hybrid or Rich
- Cannot be done by Rich with verifiable confidence

### ❓ Undefined
- Not enough information to determine owner
- This IS a flag: "Jamie needs to define this further"
- Undefined tasks should be prioritised for definition — they block the pipeline

### Owner Progression
First time doing something → 🧑 Jamie (or ❓)
Process documented, Rich can draft → 🔄 Hybrid
Process proven, output verifiable → 🤖 Rich

## Task Levels

### HEADLINES — Minimal Entry
**When:** Newly captured, early stage, simple one-off (<30 min), insufficient info to spec further.
**Required fields:**
- ID, Name, Summary
- Domain, Priority, Status, Type, Cat
- Owner
- Win State

### FULL SPEC — Complete Task File
**When:** Actively worked or planned, complex, has dependencies.
**Required fields:** All headlines PLUS:
- Subtasks — see Subtask Structure below
- Dependencies / Links (upstream + downstream)
- Layer 0 scoring (agent layer)
- Intervention stack (if B/A)
- Tools / Inputs needed

### Subtask Structure
Subtasks are the atomic units of work within a task. They follow the same output-driven principles as tasks themselves.

**Table format:**
`| # | Type | Task | Status | Owner | Output (proof of completion) |`

**Rules:**
1. **Every subtask has a defined output.** No output = can't verify completion = can't mark done.
2. **Every subtask has its own owner.** Parent may be 🔄 Hybrid while individual subtasks are 🤖 or 🧑.
3. **One output per subtask.** If it has multiple outputs, split it into multiple subtasks.
4. **Input validation before starting.** If subtask B depends on subtask A's output, A's output must verifiably exist before B starts. Otherwise B is BLOCKED.
5. **Same completion gate as tasks.** Before marking a subtask done, verify its output exists (file, column, script run, state change).
6. **Parent completion = ALL subtasks complete + win state outputs verified.** Never mark a parent done with incomplete subtasks.
7. **Note dependencies in Notes column.** E.g. "needs #3" if subtask 4 depends on subtask 3's output.

**Statuses:** CAPTURED → IN PROGRESS → COMPLETED / BLOCKED

**Validation flow for each subtask:**
```
Check inputs exist → Start work → Produce output → Verify output exists → Mark COMPLETED
       ↓ (if missing)
    Mark BLOCKED + note what's missing
```

### RTP (Repeatable Task Process) — Full Spec + Process Layer
**When:** Task recurs, has been done 2+ times, should be systematised/automated.
**Required fields:** All full spec PLUS:
- Process version (semver: v1.0, v1.1, v2.0)
- Process Version Stack (version history with what changed + why + outcome vs previous)
- Component Registry (all data objects, tools, accounts, files needed)
- Execution Log with 2+ instances
- Automation Requirements (what would need to exist to automate this)
- Maturity level (see below)

## Profiles vs Instances

### Profile
A task *type* in the registry. "Write LinkedIn Intros" is a profile. It persists and evolves.
- Lives as an entry in TASK-REGISTRY.md
- Has a canonical task file in ~/Master/tasks/
- Process steps are versioned (semver) — old versions preserved in Version Stack
- Profile evolves through accumulated instance evidence

### Instance
A single execution of a profile. "Write intros on 2026-02-20" is an instance.
- Lives as a ROW in the profile's Execution Log
- Timestamped: date, duration, outcome, deviations, friction
- Links to the process version it ran under
- NEVER overwrites the profile — it's evidence, not the process
- If an instance reveals the process needs changing → version bump on the profile

### When does a profile version bump?
- **Minor** (v1.0 → v1.1): step reordered, edge case added, resource added
- **Major** (v1.x → v2.0): fundamental restructure, steps replaced, approach changed
- Old versions preserved in Process Version Stack with "why changed" + "outcome vs previous"

## RTP Graduation

A task profile graduates to RTP when ALL RTP-level fields are filled:
- Process steps with Input/Output chains ✅
- Process version (semver) ✅
- Process Version Stack (at least v1.0 entry) ✅
- Component Registry ✅
- Execution Log with 2+ instances ✅
- Automation Requirements documented ✅

Once all fields are filled → maturity = L6 (AUTO-READY).

## Maturity Levels (for RTPs)

| Level | Name | Criteria | What Happens |
|-------|------|----------|-------------|
| L0-L5 | Pre-RTP | Not all RTP fields filled | Task is a profile, not yet an RTP |
| L6 | AUTO-READY | All RTP fields filled, automation requirements documented | Ready to build automation |
| L7 | AUTO-BUILT | Automation exists (script/cron/sub-agent) | Needs testing |
| L8 | AUTO-TESTING | Running with human verification | Track success rate |
| L9 | AUTONOMOUS | 90%+ success rate over 5+ runs, human only for exceptions | Fully autonomous |

### Maturity can drop
If automation breaks or starts failing → drop to L8 or L7. Fix, retest, re-promote.

### How maturity is assessed
The daily template scan (CLAWD-004, 16:00) checks:
1. Which RTP fields are populated → determines if L6
2. Whether automation exists → L7
3. Whether automation has run with verification → L8
4. Success rate across recent instances → L9

## Where to Find Information for Task Fields

| Field | Where to Look |
|-------|--------------|
| Domain | ~/Master/boss/ for business domains, ~/Master/domains/ for personal |
| Priority | Is it blocking revenue (🔴)? On critical path (🟡)? Can wait (⚪)? |
| Category (E/B/A/M) | Score with ~/Master/task-system/layer0-scoring.md + jamie-profile.md |
| Steps | Existing process docs, skill files in ~/clawd/skills/, reference/ files |
| Dependencies | Check TASK-REGISTRY.md for related tasks. Check task files for explicit links. |
| Tools/Inputs | What scripts, APIs, accounts, data does this need? Check ~/clawd/scripts/, skills/ |
| Intervention stack | ~/Master/task-system/intervention-drivers.md + intervention-library.md |
| Component registry | List all data objects that flow through the process steps |
| Automation requirements | What would a script/cron/agent need to do this without Jamie? |
| Win state | Ask: "How does Jamie know this is done?" — must be observable, not "worked on" |

## Dependency Types

### Hard Dependency (→)
Can't physically proceed without this. The input literally doesn't exist yet.
- "Can't send intros without intros being written"
- "Can't calculate survival maths without knowing monthly expenses"
- Notation in task files: **Hard →** [task ID]

### Soft Dependency (~>)
Makes it better / more effective, but you CAN proceed without it.
- "Offer doc makes sales calls better but you can still have conversations"
- "Dashboard is nice but you can read H1 manually"
- Notation in task files: **Soft ~>** [task ID]

### Threshold Dependency (⊕)
Proceeds when a quantitative condition is met. The upstream task doesn't "complete" — it produces signal that accumulates until a threshold triggers the downstream task.
- "Don't build course until ≥10 signups"
- "Don't invest in automation until process run 5+ times manually"
- Notation: **Threshold ⊕** [task ID] ⊕ [condition] [source: where metric lives]

**Three components:**
1. Source task — producing the signal
2. Metric + threshold — what's measured, what triggers
3. Source location — where the scanner reads the current value (H1 column, execution log count, KPI node)

**Scanner behaviour:**
- Below threshold → report: "X at 3/10. 7 to go."
- At ≥80% → flag: "X at 8/10 — start preparing."
- Met → change downstream status: WAITING → CAPTURED. Alert Jamie.

**Neo4J translation:**
```cypher
(downstream:Task)-[:DEPENDS_ON {type: 'threshold', metric: 'signups', threshold: 10, current: 3, source: 'H1:columnX'}]->(upstream:Task)
```

### How to classify
Ask: "If this upstream task didn't exist at all, could I still physically DO the downstream task?"
- NO → Hard dependency
- YES but worse → Soft dependency
- YES but only after enough signal/evidence → Threshold dependency

## Domain Operational Checklists

When Atlas traces a dependency chain to the root of a domain, it must check the domain's operational checklist before declaring "no blockers." These checklists verify that the infrastructure/tools/access for that domain are actually running.

### boss/lead-gen
- [ ] Expandi campaign active + sending CRs
- [ ] Expandi queue loaded with leads
- [ ] Expandi session connected (not expired)
- [ ] PhantomBuster cookies valid
- [ ] H1 sheet accessible + columns correct
- [ ] Intro writing skill functional (browser or PB data)
- [ ] Gmail monitoring active (CR acceptance detection)
- [ ] LinkedIn account not restricted

### boss/sales
- [ ] Offer document exists (BC-OFFER-V1)
- [ ] Call prep template exists (BC-PRECALL-PREP)
- [ ] Call notes template exists (BC-CALL-NOTES)
- [ ] Calendly / booking link active
- [ ] Payment system active (Stripe?)

### boss/product
- [ ] Program structure defined
- [ ] Onboarding process exists (BOSS-ONBOARD)
- [ ] Client app functional (BC-CLIENT-APP) — or manual alternative
- [ ] Assessment tools ready (PSS-10, PANAS)

### boss/legal-hr
- [ ] Privacy policy written
- [ ] Client contract template exists
- [ ] T&Cs written
- [ ] GDPR compliance documented

### personal/finance
- [ ] Bank access available
- [ ] All accounts/bills identified
- [ ] Spreadsheet or tool for tracking

### clawd/ops
- [ ] OpenClaw running + stable
- [ ] Cron jobs active + delivering
- [ ] Browser profile (clawd) functional
- [ ] API keys valid (Anthropic, Google, Expandi, PB)
- [ ] Master repo accessible + pushable

### Atlas Dependency Tracing Rules
When tracing upstream to find root blockers:
1. Follow HARD dependencies only for "what's physically blocking progress"
2. Note SOFT dependencies separately as "would improve effectiveness"
3. When you reach the root of a domain chain (no more upstream tasks), CHECK the domain operational checklist
4. If a checklist item is failing → THAT is the true root blocker, not any task
5. Report: "Root blocker for [domain]: [checklist item] is not operational"

## File Map — Task System Architecture

*This field guide is the central reference. Here's where everything else lives:*

| File | What It Is | When to Read |
|------|-----------|-------------|
| **task-field-guide.md** (this file) | Central reference: how to fill tasks, owner rules, deps, maturity, domain checklists, tracing | Always — this is home base |
| `pipeline.md` | Pipeline stages, gate checks, per-stage failure analysis | When advancing a task through stages |
| `template-v1.3.md` | The actual template to copy when creating a task | When creating a new task |
| `layer0-scoring.md` | 12 computational dimensions for scoring | When scoring a task (agent layer) |
| `jamie-profile.md` | Jamie's CHC/7BES profile for scoring | When scoring a task (agent layer) |
| `interventions.md` | Category routing (E/B/A/M) + pattern recognition | When a task is B/A and needs intervention |
| `intervention-library.md` | Stack composition + conflict table | When composing intervention stacks |
| `intervention-drivers.md` | Per-driver intervention menus | When selecting specific interventions |
| `checklists/README.md` | Architecture for operational checklists (hierarchy) | When building or understanding checklists |
| `checklists/global-infra.md` | Global pre-flight: APIs, gateway, browser, repos | Daily pre-flight (05:00) |
| `checklists/boss-lead-gen-expandi.md` | Full Expandi upstream pipeline checklist | When Expandi stops or lead-gen breaks |
| `~/clawd/reference/personas.md` | Atlas persona + dependency tracing rules | When doing systems/process work |
| `~/Master/TASK-REGISTRY.md` | Canonical list of all task profiles | When creating/finding/scanning tasks |
| `goal-template-v1.3.md` | Goal file template (v1.3) | When creating a new goal |
| `strategy-change-protocol.md` | Persevere vs change decision framework | During strategy reviews |
| `neo4j-schema-design.md` | Neo4J graph schema for goal/task system | When implementing graph database |
| `v1.3-lexicon.md` | Precise terminology definitions | When terms are ambiguous |

*If you can't find something, check this file map first. If it's not listed, it might not exist yet — create it.*

---

## Goal Layer (v1.3)

> Everything below is part of the MyOS `task_os` submodule specification.

### Hierarchy

```
STRATEGY LAYER
  Goal → Sub-Goal → Mechanism Chain (Outreach → Qualify → Close) → Path

EXECUTION LAYER
  Path → Task → Subtask
```

**Path** is the bridge between strategy and execution. Above it = stable strategy. Below it = volatile tasks.

Every task traces to a goal in ≤4 hops: Task → Path → MechanismStep → SubGoal → Goal.

### Foundations

The 8 irreducible infrastructure components every business needs. Assessed at goal-setting time. From BMC/Lean Canvas synthesis:

| Foundation | What It Means |
|------------|--------------|
| **Offer** | What you sell, to whom, packaged how |
| **Audience** | Who you serve + how to find them |
| **Channel** | How you reach the audience |
| **Conversion Mechanism** | How interest becomes revenue (the mechanism chain) |
| **Delivery System** | How you deliver value after sale |
| **Revenue Model** | How money flows in |
| **Legal Framework** | Permission to operate (contract, T&Cs, GDPR) |
| **Cost Structure** | What it costs to operate |

Each has a maturity state: `raw → draft → tested → proven`. Every goal file has a Foundations section assessing current state and sufficiency.

### Strategy / Execution Boundary

| If the blocker is... | It's a... | Action |
|---------------------|-----------|--------|
| Task status (CAPTURED/BLOCKED/not started) | **Execution problem** | Do the task. Unblock it. |
| Conversion ratio (doing work but not converting) | **Strategy problem** | Wait for strategy review. |
| Missing foundation | **Infrastructure problem** | Priority unblock. |
| Emotional resistance | **Behavioural problem** | Use intervention stack (EBAM). |

### Hybrid Task Subtypes

When a task is 🔄 Hybrid, classify the specific handoff pattern:

| Subtype | Meaning | Example |
|---------|---------|---------|
| 🔓 **Unblock** | Jamie does X so Rich can proceed | Jamie approves intro tone → Rich sends |
| ⚙️ **Systematise** | Jamie creates spec/skill/cron so Rich can automate forever | Jamie writes intro guidelines → Rich writes all future intros |
| 🚀 **Execute** | Jamie does something to directly produce an output | Jamie has the discovery call |

### Strategy Traffic Light

Every task gets one of these in the morning briefing. Tells you whether executing this task is strategically sound RIGHT NOW.

| Emoji | Meaning |
|-------|---------|
| ✅ | **Aligned** — strategy sound, just execute |
| ⚠️ | **Suboptimal** — strategy has gaps but proceeding anyway |
| 🔴 | **Blocked** — something upstream broken, task may be wasted effort |
| ❓ | **Undefined** — strategy not mapped for this task |

### Task Priority Traffic Light (MyOS task_os)

Determines which tasks surface first:

| Colour | Criteria | Meaning |
|--------|----------|---------|
| 🔴 Red | max(criticality, strategic_leverage) = HIGH | Must do — blocks goal or has outsized impact |
| 🟡 Amber | moderate criticality or leverage | Should do |
| 🟢 Green | low criticality + low leverage, or easy wins | Could do |

WITHIN each colour, cognitive match (EBAM category + CHC profile) determines order and intervention style. **Default ordering: worst cognitive match first** — get the hardest thing out of the way while energy is highest. The system supports personalised traffic lights per user based on their cognitive architecture.

### Task Location
Tasks are tagged: 🏠 Remote | 📍 On-site | 🔄 Either. On-site tasks can't be scheduled for remote work (e.g. gym, commute). If a task is on-site only, note what would be needed to make it remote — this feeds automation/systematisation planning.

### Morning Briefing Structure

```
## Context (auto-generated, read-only)
GOAL-001 [BUILDING]: Bottleneck at M2. 0/5 foundations sufficient.

## 🔴 Must Do
- [strategy emoji] [task] (🔓/⚙️/🚀 if hybrid) — [why]

## 🟡 Should Do
- [strategy emoji] [task] — [why]

## 🟢 Could Do
- [strategy emoji] [task] — [why]

## ⏸️ Explicitly NOT Doing
- [deferred items from goal file — active deferral, visible]
```

Three owner buckets within each priority: 🧑 Jamie only / 🤖 Rich E2E / 🔄 Hybrid (with 🔓/⚙️/🚀 subtypes).

### Weekly Review Structure

Run in strategy mode. OODA Observe + Orient + Decide phases.

1. **Strategy sense-check:** Does this still make sense?
2. **Data pull:** Update mechanism chain metrics
3. **Volume check:** Enough data to judge? (Check minimum thresholds)
4. **Mechanism chain review:** Has bottleneck moved?
5. **Signals table:** Persevere vs change (see [Strategy Change Protocol](strategy-change-protocol.md))
6. **Threshold gates:** Any approaching unlock?
7. **Path archive:** Learnings from dropped paths?
8. **Foundations:** Any maturity changes?

### OODA Cadence Discipline (from Hoshin Kanri)

| Layer | Cadence | Mode |
|-------|---------|------|
| Goals | Monthly | Strategy |
| Mechanism chains / bottleneck | Weekly | Strategy |
| Paths | Weekly | Strategy |
| Tasks | Daily | Execution |
| Environment | Quarterly | Strategy |

**Rule:** "You cannot change strategy from execution mode." Capture insights as notes, act on them in next strategy review.

### Goal Modes

| Mode | Meaning |
|------|---------|
| **BUILDING** | Active construction — creating infrastructure, defining processes |
| **OPERATIONAL** | Run mode — monitoring, exception handling, incremental optimisation. NOT structural changes |

Transition: BUILDING → OPERATIONAL when System Stop Criteria met + ≥2 weeks stable operation.

### Reference Files

| File | Purpose |
|------|---------|
| `goal-template-v1.3.md` | Template for new goal files |
| `strategy-change-protocol.md` | When to persevere vs change — linked from every goal |
| `neo4j-schema-design.md` | Graph database schema (implement when DB provisioned) |
| `v1.3-lexicon.md` | Precise definitions for all terms |

## Error Handling — Task-Level vs Centralised

Errors go in one of two places:

**Task file** (`Error Handling / Known Edge Cases` section): Errors specific to THIS task's unique process. Example: "When scraping leads with headline containing 'Dr.', the name parser strips the prefix" — this is specific to the scraping task.

**Centralised playbook** (`task-system/error-handling/[category].md`): Errors that could happen to ANY task using the same tool, cron, or infrastructure. Example: "Browser control service timeout" — any task using the browser can hit this.

**Rule:** If in doubt, put it in the centralised playbook. Task-level errors are rare and very specific. Most errors are tool/infra/cron errors that belong in the shared playbooks.

## Filing Rules

- Task files: ~/Master/tasks/[ID].md
- Registry: ~/Master/TASK-REGISTRY.md (mirrored to ~/clawd/TASK-REGISTRY.md)
- Process reference: this file (~/Master/task-system/task-field-guide.md)
- Template: ~/Master/task-system/template-v1.3.md
- Scoring: ~/Master/task-system/layer0-scoring.md
- Profile: ~/Master/task-system/jamie-profile.md
