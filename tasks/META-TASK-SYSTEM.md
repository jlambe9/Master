# META-TASK-SYSTEM — Expand Task Tracker to v1.2

> **Summary:** Upgrade task tracking system with auto-scoring, completion gates, pipeline wiring, and daily planning.

**Domain:** meta/task-system
**Priority:** 🟡 HIGH
**Status:** IN PROGRESS
**Type:** EXPLORE
**Cat:** 🟢 E
**Owner:** 🤖 Rich
**Maturity:** L3
**Next Action:** #23 (H1 fields) + #11 (maturity scan script)
**Created:** 2026-02-10
**Pipeline:** v1.2
**Field Guide:** task-system/task-field-guide.md

## Dependencies
**Hard →:** None (root task)
**Soft ~>:** CLAWD-003 (KPI dashboard), LP-006 (pipeline data feeds daily planning)
**Downstream (blocks):** Daily planning skill, CLAWD-004 (scan), LP-001→006 (pipeline tasks use this template)
**Domain checklist:** meta/task-system

## Win State
Task system v1.2 operational with completion gates, pipeline integration, and automated daily planning.

**Outputs (completion gate — ALL must exist to mark done):**
1. `template-v1.2.md` exists with completion gate fields ✅
2. `task-field-guide.md` documents completion gate protocol ✅
3. `AGENTS.md` Step 5 enforces completion verification ✅
4. All task files in v1.2 format (Output columns in Steps + Subtasks)
5. `TASK-REGISTRY.md` current with all tasks including LP-001→006
6. `linkedin-pipeline-wiring.md` maps stages → tasks → scripts → H1 ✅
7. CLAWD-004 scan script runs and identifies non-compliant tasks
8. Daily planning skill produces 3-bucket plan with real pipeline data
9. H1 has all priority columns for pipeline tracking

## Steps
| # | Input | Action | Output (proof of completion) |
|---|-------|--------|----------------------------|
| 1 | Layer 0 scoring + Jamie profile | Design gate integration | `pipeline.md` v1.1 ✅ |
| 2 | pipeline.md | Create template v1.2 | `template-v1.2.md` exists ✅ |
| 3 | Template | Reformat all tasks | All files in ~/Master/tasks/ match v1.2 |
| 4 | Formatted tasks | Populate registry | `TASK-REGISTRY.md` current ✅ |
| 5 | v0.2 pipeline spec + stages | Reconcile + create wiring doc | `linkedin-pipeline-wiring.md` exists ✅ |
| 6 | Wiring doc | Create LP-001→006 tasks | 6 task files in ~/Master/tasks/ ✅ |
| 7 | H1 current columns | Define + add priority columns | H1 has aiPassed, jamieReviewed, sendMessage, pipelineStage, screenResult |
| 8 | Field guide + template | Build CLAWD-004 scan script | `scripts/task-scan.js` runs without error |
| 9 | Pipeline data + task data | Build daily planning skill | Skill produces 3-bucket plan from real data |

## Subtasks
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 1 | EXPLORE | Review Layer 0 scoring for gate integration | COMPLETED | 🤖 | pipeline.md v1.1 |
| 2 | EXPLORE | Define expanded stage requirements | COMPLETED | 🤖 | pipeline.md stages section |
| 3 | EXPLOIT | Update pipeline.md with v1.1 definitions | COMPLETED | 🤖 | pipeline.md v1.1.0 |
| 4 | EXPLOIT | Update template to v1.2 | COMPLETED | 🤖 | `template-v1.2.md` exists with Output columns + completion gate |
| 5 | EXPLOIT | Validate v1.2 with first real task | CAPTURED | 🤖 | One task created using v1.2 + completion gate verified |
| 6 | EXPLOIT | Create Task Registry | COMPLETED | 🤖 | `TASK-REGISTRY.md` exists + mirrored |
| 7 | EXPLOIT | Scan all tasks → populate registry | COMPLETED | 🤖 | All 31 tasks reformatted by Atlas |
| 8 | EXPLOIT | Define Owner field spec + add to template | COMPLETED | 🤖 | Owner field in template + field guide + AGENTS.md |
| 9 | EXPLOIT | Define 3-bucket daily planning structure | BLOCKED | 🤖 | Skill produces 3-bucket plan → needs #5, #11, LP-006 #8-9 |
| 10 | EXPLOIT | Define instance vs profile distinction | COMPLETED | 🤖 | task-field-guide.md documents it |
| 11 | EXPLOIT | Build CLAWD-004 maturity scan script | CAPTURED | 🤖 | `scripts/task-scan.js` runs + outputs non-compliant tasks |
| 12 | EXPLOIT | Daily planning = evening before | BLOCKED | 🤖 | Cron fires at 21:00, skill works → needs #9 |
| 13 | EXPLOIT | Create task-field-guide.md | COMPLETED | 🤖 | File exists with owner, levels, RTP, maturity, completion gate |
| 14 | EXPLOIT | Update template — Owner, Maturity, RTP, Completion Gate | COMPLETED | 🤖 | template-v1.2.md has all sections |
| 15 | EXPLOIT | Build daily-planning skill | BLOCKED | 🤖 | Skeleton at skills/daily-planning/SKILL.md → needs #9 resolved |
| 16 | EXPLOIT | Create daily-planning cron (21:00) | COMPLETED | 🤖 | Cron exists and fires |
| 17 | EXPLOIT | Add dependency types to template + field guide | COMPLETED | 🤖 | Hard/soft/threshold in template + field guide |
| 18 | EXPLOIT | Create domain/subdomain operational checklists | COMPLETED | 🔄 | global-infra.md + boss-lead-gen-expandi.md |
| 19 | EXPLOIT | Update Atlas persona with dependency tracing rules | COMPLETED | 🤖 | personas.md updated |
| 20 | EXPLORE | Build in Mud — threshold deps | COMPLETED | 🤖 | Threshold deps (⊕) in template + field guide + Neo4J schema |
| 21 | EXPLOIT | Expandi upstream checklist | COMPLETED | 🤖 | checklists/boss-lead-gen-expandi.md |
| 22 | EXPLOIT | Reconcile pipeline spec + create LP tasks | COMPLETED | 🤖 | linkedin-pipeline-wiring.md + LP-001→006 in registry |
| 23 | — | MOVED → LP-006 #8 (H1 fields) | — | — | Not a task system concern |
| 24 | — | MOVED → LP-006 #9 (pipeline status script) | — | — | Not a task system concern |
| 25 | — | MOVED → LP-006 #10 (pipeline stats → KPIs) | — | — | Not a task system concern |
| 26 | EXPLOIT | Completion gate enforcement | COMPLETED | 🤖 | AGENTS.md Step 5 + template Output columns |
| 27 | EXPLOIT | Reformat all tasks to v1.2 | COMPLETED | 🤖 | 37 files: Steps removed, Output columns added, completion gates |
| 28 | EXPLORE | v1.3 Goal layer design (Atlas framework) | IN PROGRESS | 🔄 | Draft + 3 critiques + lexicon + frameworks research complete. Final synthesis pending. |
| 29 | EXPLOIT | Define traffic light task prioritisation schema | CAPTURED | 🔄 | Red/Amber/Green from: criticality × strategic leverage × cognitive match. For MyOS task_os. |
| 30 | EXPLOIT | Define morning briefing structure | CAPTURED | 🔄 | Strategy emoji per task + 3 buckets (🧑/🤖/🔄 with 🔓/⚙️/🚀) + "NOT doing" section |
| 31 | EXPLOIT | Define weekly review structure | CAPTURED | 🔄 | Strategy sense-check, data pull, minimum volume thresholds, mechanism chain review |
| 32 | EXPLOIT | Define strategy/execution boundary | CAPTURED | 🤖 | Where does a trace stop being strategic and become execution? Task status = execution, conversion ratio = strategy |
| 33 | EXPLOIT | Document hybrid task subtypes in field guide | CAPTURED | 🤖 | 🔓 Unblock / ⚙️ Systematise / 🚀 Execute |
| 34 | EXPLOIT | Build strategic alignment cron | CAPTURED | 🤖 | Weekly cron: trace goals → verify execution serves current bottleneck |
| 35 | EXPLOIT | Build execution monitoring cron | CAPTURED | 🤖 | Daily cron: check task statuses, flag stalled/blocked, produce morning briefing |
| 36 | EXPLOIT | Reformat all tasks to v1.3 | CAPTURED | 🤖 | All task files have Goal field, Location field, Decision Log section. template-v1.3.md used as reference. |
| 37 | EXPLORE | v1.3 system overview document | COMPLETED | 🤖 | `v1.3-system-overview.md` exists with all 10 sections + 4 appendices |
| 38 | EXPLORE | Process leak vulnerability audit (10 vulnerabilities) | COMPLETED | 🤖 | `v1.3-vulnerability-audit.md` exists with all 10 failure modes + enforcement specs |
| 39 | EXPLORE | Cron map audit (24 crons reviewed) | COMPLETED | 🤖 | `v1.3-cron-registry.md` exists with all 24 crons mapped, prioritised, dependency chain |
| 40 | EXPLORE | Enforcement rules audit (AGENTS.md/SOUL.md gaps) | COMPLETED | 🤖 | `v1.3-enforcement-rules.md` exists with 5 new sections, 4 modifications, SOUL.md additions |
| 41 | EXPLOIT | Add cron classification (system/domain) to system overview + cron registry | IN PROGRESS | 🤖 | System overview §11 has Cron Classification table. Cron registry has Scope field on every cron. |
| 42 | EXPLOIT | Implement enforcement rules into AGENTS.md | CAPTURED | 🤖 | AGENTS.md has: Goal Creation Protocol, Goal Linkage (Step 6b), Hybrid Subtypes (Step 3c), Strategy/Execution Boundary, Morning Briefing Protocol, Weekly Review Triggers, template ref → v1.3 |
| 43 | EXPLOIT | Implement enforcement additions to SOUL.md | CAPTURED | 🤖 | SOUL.md has System Discipline section (stick-to-plan, don't over-map, one bottleneck) |
| 44 | EXPLOIT | Add automation enforcement section to system overview | CAPTURED | 🤖 | System overview has §11 Automation Enforcement with: cron classification, model tiers, consolidated cron table, dependency map |
| 45 | EXPLOIT | Build/consolidate all 10 crons with model tier assignments | CAPTURED | 🤖 | 10 crons exist in OpenClaw with correct models. Old redundant crons removed. |
| 46 | EXPLOIT | Add model tier system to system overview + AGENTS.md | CAPTURED | 🤖 | System overview + AGENTS.md define 3 model tiers (Strategy/Judgment/Validation) with assignment rules |

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|
| 2026-02-20 | v1.1 design + implementation | pipeline.md + template-v1.1.md | ~30min |
| 2026-02-21 | Atlas: 31 tasks reformatted to v1.1 | All scored, owner-tagged | ~1h |
| 2026-02-21 | Template upgraded to v1.2 | Completion gate + Output columns added | ~10min |
| 2026-02-21 | Completion gate protocol written | AGENTS.md Step 5 + field guide | ~15min |
| 2026-02-21 | Atlas: Pipeline reconciliation | Wiring doc + LP-001→006 created | ~5min |
| 2026-02-21 | H1 columns clarified | aiPassed, jamieReviewed, sendMessage defined | ~10min |
| 2026-02-21 | META-TASK-SYSTEM reformatted to v1.2 | This file | ~5min |

## Source Documents
- task-system/layer0-scoring.md
- task-system/interventions.md
- task-system/intervention-library.md
- task-system/intervention-drivers.md
- task-system/jamie-profile.md
- task-system/lead-pipeline-stages.md
- task-system/linkedin-pipeline-wiring.md

## KPI / How We Measure
- Time-to-execution for new tasks <5 min
- Prediction accuracy: predicted vs actual E/B/A/M match rate
- Completion gate catch rate: % of tasks with vague/missing outputs flagged before false completion

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
| 1.2 | 2026-02-21 | Completion gate, Output columns, pipeline reconciliation | Rich |

## Notes
- LP-006 #8-9 (H1 columns + pipeline status script) is a priority test case for validating the task system with real data, but it's not owned by META-TASK-SYSTEM. The task system is domain-agnostic — it won't always be outputting LinkedIn data.
