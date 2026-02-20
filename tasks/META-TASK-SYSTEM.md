# META-TASK-SYSTEM — Expand Task Tracker to v1.1

> **Summary:** Upgrade the task tracking system to automatically score tasks using Jamie's cognitive profile (12 dimensions, channel matching, emotional load) instead of manual classification.

**Domain:** meta/task-system
**Priority:** 🟡 HIGH
**Status:** IN PROGRESS
**Type:** EXPLORE
**Cat:** 🟢 E
**Next Action:** Review v1.1 pipeline and template, validate with first real task
**Created:** 2026-02-10
**Pipeline:** v1.1

## Win State
Task pipeline expanded from v1.0 (8 stages + simple gate checks) to v1.1 with full Layer 0 scoring integration, per-stage failure analysis, and intervention auto-selection.

## What v1.1 adds over v1.0
- Full Layer 0 computational scoring (12 dimensions) integrated into gate checks
- Channel requirement analysis (CHC mapping) at DECOMPOSED stage
- Affective load scoring at GOAL CLARITY stage (early A-task detection)
- Per-stage failure analysis with intervention auto-selection
- Layer 3 prediction formula applied at PLANNED stage
- Agent auto-advancement: agents fill gates, not Jamie
- Outcome vs prediction tracking at COMPLETED stage
- Process versioning (semver) for pipeline itself
- Jamie's view reduced to: name, status, priority, next action, category emoji

## Source Documents (already in /master)
- `task-system/layer0-scoring.md` — 12 computational dimensions (0A), channel requirements (0B), affective load (0C), Layer 3 formula
- `task-system/interventions.md` — pipeline failure points table, pattern recognition triggers
- `task-system/intervention-library.md` — stack composition, conflict table
- `task-system/intervention-drivers.md` — 6 aversion driver menus
- `task-system/jamie-profile.md` — CHC capacities, 7BES thresholds, pharma context

## KPI / How We Measure
- Time-to-execution for new tasks <5 min (from seeing sequence to starting)
- Prediction accuracy: predicted vs actual E/B/A/M category match rate

## Subtasks
| # | Type | Task | Status | Notes |
|---|------|------|--------|-------|
| 1 | EXPLORE | Review Layer 0 scoring for gate check integration points | COMPLETED | Integrated into pipeline.md v1.1 |
| 2 | EXPLORE | Define expanded stage requirements with computational thresholds | COMPLETED | Per-stage failure analysis + auto-intervention in pipeline.md |
| 3 | EXPLOIT | Update pipeline.md with v1.1 definitions | COMPLETED | v1.1.0, 2026-02-20 |
| 4 | EXPLOIT | Update templates/task.md with new fields | COMPLETED | template-v1.1.md created |
| 5 | EXPLOIT | Validate v1.1 with first real task | CAPTURED | Next step |
| 6 | EXPLOIT | Create Task Registry — canonical library of all task types/profiles by domain/subdomain | IN PROGRESS | ~/Master/TASK-REGISTRY.md, mirrored to ~/clawd/TASK-REGISTRY.md |
| 7 | EXPLOIT | Scan all existing tasks → populate registry with correctly formatted profiles | IN PROGRESS | 30 task files to scan |
| 8 | EXPLORE | Define Owner field spec (Jamie/Rich/Hybrid/Undefined) + add to template | CAPTURED | Who executes — determines daily bucket |
| 9 | EXPLORE | Define 3-bucket daily planning structure (Rich E2E / Rich+Jamie handoff / Jamie only) | CAPTURED | Feeds into morning planning session |
| 10 | EXPLORE | Define instance vs profile distinction — process for any agent to follow | CAPTURED | When does a task instance become a profile? When does a profile become an RTP? |
| 11 | EXPLOIT | Build maturity scan task — scan all tasks, identify missing RTP sections, create remediation tasks | CAPTURED | Not a cron yet — manual fire each evening |
| 12 | EXPLORE | Define daily planning session format — reverse-engineer from goals → outputs → tasks → schedule | CAPTURED | The actual morning workflow |

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|
| 2026-02-20 | Atlas: Full v1.1 design and implementation | pipeline.md rewritten, template-v1.1.md created, subtasks 1-4 completed | ~30min |

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🟢 E | 🟢 E |
| Failure point | Decomposition | None so far |
| Duration | 2h | ~30min |
| Intervention | None needed (E-task) | None needed |
| Effectiveness | — | — |

## Notes
- v1.0 was deliberately simple: 8 stages, text-based gate checks, 3 priority levels, 3 task types
- v1.1 integrates computational scoring WITHOUT making daily use harder
- Key insight: the system failed because it required Jamie to maintain it. v1.1 puts ALL maintenance on agents.
- **Design principle:** If Jamie has to fill a field, the system will be abandoned. Agents fill everything. Jamie confirms or overrides.

## Analysis: Why v1.0 Stalled

**Why tasks stay at CAPTURED:**
- No automated advancement. Agent sees CAPTURED but has no mandate to auto-score and advance.
- Gate checks require Jamie to write win states, decompose steps — executive function tasks that are themselves B/A tasks.
- The pipeline is a meta-task that competes with the actual task for cognitive resources.

**Why fields don't get filled:**
- Glr at 2nd percentile means Jamie cannot encode "fill in these fields" as a habit without extreme repetition.
- The fields feel like bureaucracy (B-task) wrapping the real task. SEEKING disengages.
- No feedback loop: filling fields produces no visible reward.

**Why Jamie defaults to not tracking:**
- Tracking is a B-task. The system designed to manage B-tasks is itself a B-task.
- The only way out: agents do the tracking. Jamie's only job is to say what he wants done and confirm when it's done.

**v1.1 fix:** Agent auto-scores at CAPTURED, auto-advances through gates it can fill, asks Jamie exactly ONE question when stuck, and reduces Jamie's view to 4 fields.
