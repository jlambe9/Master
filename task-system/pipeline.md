# Task Pipeline v1.0 — Canonical Variables

*Reference file. Any agent checking a task's status reads this to know what's valid.*

## Status (Pipeline Stages)

| Stage | Gate Check (task file must have...) |
|-------|--------------------------------------|
| CAPTURED | Exists. Has a name. |
| GOAL CLARITY | Win state defined |
| DECOMPOSED | Steps listed OR link to process in PROCESSES.md |
| SEQUENCED | Dependencies mapped, order defined |
| PLANNED | Time estimate + slot assigned |
| INITIATED | In STATUS.md active (max 3) |
| IN PROGRESS | Execution log started |
| COMPLETED | Outcome logged |
| PERSISTED | Learnings captured, context saved |
| BLOCKED | Blocker field filled (can happen at any stage) |

*Agent enforcement: if a field is missing, the task cannot advance past that gate.*

## Priority

| Level | Meaning |
|-------|---------|
| 🔴 CRITICAL | Blocks revenue or hard deadline |
| 🟡 HIGH | On critical path |
| ⚪ MEDIUM | Important, can wait |

## Task Type

| Type | Output | Example |
|------|--------|---------|
| EXPLORE | Knowledge, process map, decision | "Figure out how to file HMRC taxes" |
| EXPLOIT | Deliverable using known process | "Upload receipts to HMRC portal" |
| ADMIN | Routine done/not-done | "Update Neo4j payment" |

## E/B/A/M Category (orthogonal to pipeline)

| Cat | When to assign |
|-----|---------------|
| 🟢 E | High epistemic value, SEEKING engaged |
| 🟡 B | Low novelty, draining — check eliminate/automate/delegate first |
| 🔴 A-S | Emotionally aversive but structurally fixable |
| 🔴 A-I | Intrinsically aversive — growth+support or delegate |
| 🟠 M | Going through wrong cognitive channel — reroute |

*Full scoring: task-system/layer0-scoring.md. Interventions: task-system/interventions.md.*

## Subtask Rules

- Subtasks are rows in the parent task file, not separate files
- Each subtask has its own Type and Status
- Parent can't be COMPLETED until all subtasks are COMPLETED or N/A
- Subtasks can mix types (EXPLORE + EXPLOIT in same parent)

## v1.1 Expansion (queued)

See task META-TASK-SYSTEM for links to:
- Full Layer 0 scoring (12 computational + channel + affective dimensions)
- Layer 3 prediction formula
- Expanded pipeline failure point analysis per stage
- Intervention stack composition for each failure point
