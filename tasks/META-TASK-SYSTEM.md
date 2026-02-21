# META-TASK-SYSTEM — Expand Task Tracker to v1.1

> **Summary:** Upgrade task tracking system to auto-score tasks using Jamie's cognitive profile instead of manual classification.

**Domain:** meta/task-system
**Priority:** 🟡 HIGH
**Status:** IN PROGRESS
**Type:** EXPLORE
**Cat:** 🟢 E
**Owner:** 🤖 Rich
**Next Action:** Complete subtask 7 (scan all tasks → populate registry) — currently running as Atlas reformat
**Created:** 2026-02-10
**Pipeline:** v1.1

## Win State
Task pipeline expanded from v1.0 to v1.1 with full Layer 0 scoring, per-stage failure analysis, intervention auto-selection, and outcome tracking.

## What v1.1 Adds
- Full Layer 0 computational scoring (12 dimensions) at gate checks
- Channel requirement analysis (CHC mapping) at DECOMPOSED
- Affective load scoring at GOAL CLARITY (early A-task detection)
- Per-stage failure analysis with intervention auto-selection
- Layer 3 prediction at PLANNED
- Agent auto-advancement through gates
- Outcome vs prediction tracking at COMPLETED
- Process versioning (semver) for pipeline
- Jamie's view reduced to: name, status, priority, next action, category emoji

## Subtasks
| # | Type | Task | Status | Owner | Notes |
|---|------|------|--------|-------|-------|
| 1 | EXPLORE | Review Layer 0 scoring for gate integration | COMPLETED | 🤖 | |
| 2 | EXPLORE | Define expanded stage requirements | COMPLETED | 🤖 | |
| 3 | EXPLOIT | Update pipeline.md with v1.1 definitions | COMPLETED | 🤖 | v1.1.0, 2026-02-20 |
| 4 | EXPLOIT | Update template with new fields | COMPLETED | 🤖 | template-v1.1.md |
| 5 | EXPLOIT | Validate v1.1 with first real task | CAPTURED | 🤖 | Next |
| 6 | EXPLOIT | Create Task Registry | IN PROGRESS | 🤖 | TASK-REGISTRY.md |
| 7 | EXPLOIT | Scan all tasks → populate registry | IN PROGRESS | 🤖 | Atlas reformat running |
| 8 | EXPLOIT | Define Owner field spec + add to template | COMPLETED | 🤖 | task-field-guide.md + AGENTS.md + template |
| 9 | EXPLOIT | Define 3-bucket daily planning structure | IN PROGRESS | 🤖 | Skill being built |
| 10 | EXPLOIT | Define instance vs profile distinction | COMPLETED | 🤖 | task-field-guide.md: profiles versioned, instances = exec log rows |
| 11 | EXPLOIT | Build maturity scan (CLAWD-004) | CAPTURED | 🤖 | Needs field-guide + RTP sections defined first |
| 12 | EXPLOIT | Daily planning = evening before, not morning | IN PROGRESS | 🤖 | Part of daily-planning skill |
| 13 | EXPLOIT | Create task-field-guide.md | COMPLETED | 🤖 | Owner, levels, RTP graduation, maturity |
| 14 | EXPLOIT | Update template — Owner, Maturity, RTP sections | COMPLETED | 🤖 | Process version stack, component registry, automation reqs |
| 15 | EXPLOIT | Build daily-planning skill | IN PROGRESS | 🤖 | Evening scan → 3 buckets → tomorrow's outputs |
| 16 | EXPLOIT | Create daily-planning cron (21:00) | CAPTURED | 🤖 | Depends on skill (#15) |
| 17 | EXPLOIT | Add hard vs soft dependency distinction to template + field guide | CAPTURED | 🤖 | Hard = can't proceed without. Soft = improves but not required. |
| 18 | EXPLOIT | Create domain/subdomain operational checklists | CAPTURED | 🔄 | Each domain has a "is this actually running?" checklist. Atlas checks these when tracing to root of a chain. |
| 19 | EXPLOIT | Update Atlas persona with dependency tracing rules | CAPTURED | 🤖 | When Atlas hits root of a chain → check domain checklist → verify infrastructure is online |
| 20 | EXPLORE | Build in Mud mode — threshold-based dependencies, dynamic scanning, wicked problem design | IN PROGRESS | 🤖 | Atlas design task. How to track moving parts in dynamic system. Must be Neo4J-translatable. |
| 21 | EXPLOIT | Expandi upstream checklist — full flow diagram from leads→validated→scraped→screened→intros written→reviewed(AI)→reviewed(Jamie)→uploaded→campaign active | CAPTURED | 🤖 | Subtask of LinkedIn outreach subdomain. "What to check when Expandi stops" |

## Steps (Input → Action → Output)
1. **Input:** Layer 0 scoring docs + Jamie's profile → **Action:** Design gate integration → **Output:** pipeline.md v1.1 (DONE)
2. **Input:** pipeline.md + scoring → **Action:** Create v1.1 template → **Output:** template-v1.1.md (DONE)
3. **Input:** Template → **Action:** Scan all 31 task files, reformat → **Output:** All tasks in v1.1 format (IN PROGRESS)
4. **Input:** Reformatted tasks → **Action:** Update TASK-REGISTRY.md → **Output:** Current registry
5. **Input:** Registry → **Action:** Build CLAWD-004 (daily scan cron) → **Output:** Automated maintenance

## Dependencies / Links
- **Upstream:** task-system/*.md (scoring docs, Jamie's profile)
- **Downstream:** All task files (formatted by this), CLAWD-004 (maintains format), daily planning

## Source Documents
- task-system/layer0-scoring.md
- task-system/interventions.md
- task-system/intervention-library.md
- task-system/intervention-drivers.md
- task-system/jamie-profile.md

## KPI / How We Measure
- Time-to-execution for new tasks <5 min
- Prediction accuracy: predicted vs actual E/B/A/M match rate

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|
| 2026-02-20 | Atlas: Full v1.1 design and implementation | pipeline.md + template-v1.1.md created | ~30min |
| 2026-02-21 | Atlas: All 31 tasks reformatted to v1.1 | Scored, owner-tagged, process-mapped | ~1h |

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🟢 E | 🟢 E |
| Failure point | Decomposition | None so far |
| Duration | 2h | ~1.5h total |
| Intervention | None needed (E-task) | None needed |
| Effectiveness | — | — |

## Analysis: Why v1.0 Stalled
- No automated advancement — agents had no mandate to auto-score
- Gate checks required Jamie to do executive function tasks (B/A tasks themselves)
- Fields felt like bureaucracy wrapping the real task
- No feedback loop from filling fields
- **v1.1 fix:** Agent auto-scores, auto-advances, asks Jamie exactly ONE question when stuck. Jamie's view = 4 fields.

## Decision Log
- 2026-02-20: v1.1 designed and implemented. pipeline.md rewritten, template-v1.1.md created.
- 2026-02-21: Atlas reformatted all 31 task files to v1.1 template.

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | High | Novel system design |
| Procedure specification | Partial | Design principles clear, implementation evolving |
| Procedure complexity | Complex | Multi-component system |
| Temporal delay | Weeks | Build → validate → iterate |
| Error cost | Reversible | System can be updated |
| Reward magnitude | High | Foundation of all task management |
| Reward probability | Likely | Each component delivers value |
| Value density per unit | High | System thinking = high engagement |
| Feedback latency | Delayed | Validated over weeks |
| Process legibility | Partial | Complex system design |
| Model maturity | Novel | First time |
| State-tracking load | High | Many components |

### 0B: Channel Requirements
- **Input route:** Reading + semantic (Gc,Gf)
- **Processing route:** Pattern detection + simultaneous (Gf,Gwm)
- **Output route:** Writing (Gc,Grw)
- **Channel flexible:** Y — Rich E2E
- **Mismatch flags:** None

### 0C: Affective Load
All dimensions: N / —

### Layer 3 Computation
- **Epistemic value:** High → **Pragmatic value:** High → **Effort cost:** Med → **Threat:** None
- **Dominant signal:** → 🟢 E

### Predicted Failure Point
- **Stage:** In-progress (scope creep)
- **Cause:** System design is an E-task that can absorb unlimited time
- **Auto-intervention:** Agent flags time-on-task vs revenue work

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-10 | Created | Rich |
| 1.1 | 2026-02-21 | Reformatted to v1.1 | Atlas |
