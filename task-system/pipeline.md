# Task Pipeline v1.1 — Canonical Variables

*Process version: 1.1.0 (2026-02-20)*
*Changelog: v1.0→v1.1: Agent auto-scoring, per-stage failure analysis, outcome tracking, process versioning.*

## Status (Pipeline Stages)

| Stage | Gate Check | Agent Auto-Action |
|-------|-----------|-------------------|
| CAPTURED | Exists. Has a name. | Auto-score Layer 0 (0A+0B+0C). Assign E/B/A/M. Set priority. Predict failure point. |
| GOAL CLARITY | Win state defined | Score affective load (0C). Flag A-tasks early. Suggest intervention stack if A. |
| DECOMPOSED | Steps listed OR link to PROCESSES.md | Map CHC channel requirements (0B). Flag M-tasks (channel mismatch). |
| SEQUENCED | Dependencies mapped, order defined | Auto-sequence if ≤5 steps. Flag blocking dependencies. |
| PLANNED | Time estimate + slot assigned | Apply Layer 3 prediction. Log prediction snapshot. |
| INITIATED | In STATUS.md active (max 3) | Check initiation conditions (energy, time, pharma window). |
| IN PROGRESS | Execution log started | Monitor for stall (>2× estimated duration → surface). |
| COMPLETED | Outcome logged | Compare prediction vs actual. Update task-log.md profile. |
| PERSISTED | Learnings captured | Update intervention confidence levels. Feed experiments. |
| BLOCKED | Blocker field filled | Auto-suggest unblock path. Escalate after 48h. |

### Gate Enforcement (Agent Layer)

When agent encounters a task, it checks the current stage's gate. If gate not met:
1. **Can agent fill it?** → Fill it. Don't ask Jamie.
2. **Needs Jamie input?** → Ask ONE specific question. Not a form.
3. **Blocked on external?** → Mark BLOCKED with blocker.

**Auto-advance rule:** If agent fills a gate, advance the task silently. Jamie sees current status, not the journey.

## Priority

| Level | Meaning | Auto-Assignment Signal |
|-------|---------|----------------------|
| 🔴 CRITICAL | Blocks revenue or hard deadline | Deadline <48h OR revenue-blocking dependency |
| 🟡 HIGH | On critical path | Deadline <1 week OR blocks other tasks |
| ⚪ MEDIUM | Important, can wait | Everything else |

## Task Type

| Type | Output | Example |
|------|--------|---------|
| EXPLORE | Knowledge, process map, decision | "Figure out how to file HMRC taxes" |
| EXPLOIT | Deliverable using known process | "Upload receipts to HMRC portal" |
| ADMIN | Routine done/not-done | "Update Neo4j payment" |

## E/B/A/M Category (agent-computed at CAPTURED)

| Cat | Auto-Assignment Rule |
|-----|---------------------|
| 🟢 E | Epistemic value > effort cost AND epistemic value > pragmatic value |
| 🟡 B | Pragmatic value > epistemic value AND threat < threshold |
| 🔴 A-S | Threat signal present AND procedure specification ≥ Partial |
| 🔴 A-I | Threat signal present AND procedure specification = Open OR affective load High on ≥2 dimensions |
| 🟠 M | CHC mismatch detected (task requires Jamie's weak channels without alternative route) |

*Layer 3 formula (from layer0-scoring.md) produces numerical scores. Category = highest signal.*

## Per-Stage Failure Analysis

| Stage | Failure Signal | Auto-Intervention |
|-------|---------------|-------------------|
| GOAL CLARITY | Jamie can't articulate "done" | Agent proposes 3 candidate win states → Jamie picks one |
| DECOMPOSED | >3 days at this stage | Agent decomposes using PROCESSES.md or generates steps |
| SEQUENCED | Circular dependencies or >10 steps | Agent simplifies: group into phases of 3-5 |
| PLANNED | No slot assigned within 48h | Agent suggests specific slot based on energy pattern + calendar |
| INITIATED | Task in PLANNED >48h, not started | Surface: "Start [task] now? First action: [X]" — one tap |
| IN PROGRESS | Duration >2× estimate | Check: WM overload? Encoding failure? Energy? → Suggest break/restructure |
| COMPLETED | Task done but no outcome logged | Agent prompts: "How did [task] go? 1 word." |
| PERSISTED | No learnings after COMPLETED | Agent auto-generates learnings from execution data. Jamie confirms. |

## Subtask Rules

- Subtasks are rows in the parent task file, not separate files
- Each subtask has its own Type and Status
- Parent can't be COMPLETED until all subtasks are COMPLETED or N/A
- Subtasks can mix types (EXPLORE + EXPLOIT in same parent)

## Outcome Tracking

After COMPLETED, agent logs:
```
Predicted: [E/B/A/M] → Actual: [E/B/A/M]
Predicted failure point: [stage] → Actual: [stage or "none"]
Predicted duration: [X] → Actual: [Y]
Intervention used: [stack] → Effectiveness: [1-word from Jamie]
```
Deviations >1 category trigger model review flag in `experiments.md`.

## Process Versioning

Pipeline itself is versioned (this file header). Changes follow semver:
- **Patch** (1.1.x): Wording, clarification, no behavioral change
- **Minor** (1.x.0): New field, new auto-action, new stage gate — backward compatible
- **Major** (x.0.0): Stage restructure, breaking template changes

All task files created under a version remain valid. Agent handles migration.

## Jamie's View (What Jamie Actually Sees)

| Field | Source |
|-------|--------|
| Task name | Jamie or agent |
| Status | Auto-tracked |
| Priority | Auto-assigned (Jamie can override) |
| Next action | Agent-generated from current stage |
| Category emoji | Auto-assigned |

Everything else (Layer 0 scores, channel maps, affective dimensions, intervention stacks) lives in the task file's agent section. Jamie never needs to read it.
