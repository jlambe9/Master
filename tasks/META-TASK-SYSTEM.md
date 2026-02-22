# META-TASK-SYSTEM — Task Manager System v1.3

> **Summary:** Full task management system with goals, mechanisms, enforcement, error handling, cron infrastructure, and BPMN-ready process definitions. North star: every process formalised to DAG-portable notation.

**Domain:** meta/task-system
**Priority:** 🔴 CRITICAL
**Status:** IN PROGRESS
**Type:** EXPLORE
**Cat:** 🟢 E
**Owner:** 🤖 Rich
**Maturity:** L3
**Next Action:** Phase 1 (#42, #43, #46, #47, #48, #49, #50)
**Created:** 2026-02-10
**Pipeline:** v1.3
**Field Guide:** task-system/task-field-guide.md
**Goal:** STANDALONE | Meta-system — enables all other goals

## Dependencies
**Hard →:** None (root task)
**Soft ~>:** CLAWD-003 (KPI dashboard), LP-006 (pipeline data feeds daily planning)
**Downstream (blocks):** Daily planning skill, CLAWD-004 (scan), LP-001→006 (pipeline tasks use this template)
**Domain checklist:** meta/task-system

## Win State
Task management system v1.3 operational with: goal layer, enforcement rules, error handling, 10 consolidated crons, all tasks v1.3 compliant, and every process written in BPMN-ready notation portable to DAG.

**Outputs (completion gate — ALL must exist to mark done):**
1. `template-v1.3.md` exists with Goal, Location, Decision Log fields ✅
2. `goal-template-v1.3.md` exists with foundations, mechanisms, paths, gates ✅
3. `v1.3-system-overview.md` exists with all sections including §11 Automation Enforcement ✅ (partial)
4. `AGENTS.md` enforces v1.3: goal creation protocol, goal linkage, hybrid subtypes, strategy/execution boundary, model tiers, BPMN north star
5. `SOUL.md` has system discipline + BPMN formalisation north star
6. `v1.3-cron-registry.md` has all 10 crons with: scope, model tier, inputs, outputs, error handling, cron template definition
7. `error-playbook.md` exists with structured error categories + resolution procedures
8. 10 consolidated crons live in OpenClaw with correct models, sequential execution, error handling
9. All task files in v1.3 format (Goal, Location, Decision Log)
10. GOAL-001 exists as worked example through full system
11. All processes expressed in BPMN notation (trigger → activities → gateways → outputs → error boundaries) — Phase 6
12. All BPMN definitions encoded as DAG (JSON/YAML, machine-readable, no prose) — Phase 7
13. Complete DAG package ready for MyOS task_os handoff — Phase 7

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
### Phase 0 — Foundation (v1.0→v1.2) [COMPLETED]
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

### Phase 1 — v1.3 Design & Audit [COMPLETED]
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 28 | EXPLORE | v1.3 Goal layer design (Atlas framework) | COMPLETED | 🔄 | goal-template-v1.3.md + strategy-change-protocol.md + lexicon + field guide updated |
| 29 | EXPLOIT | Define traffic light task prioritisation schema | COMPLETED | 🔄 | Defined in v1.3-system-overview.md §7.1 + field guide |
| 30 | EXPLOIT | Define morning briefing structure | COMPLETED | 🔄 | Defined in v1.3-system-overview.md §7.1 |
| 31 | EXPLOIT | Define weekly review structure | COMPLETED | 🔄 | Defined in v1.3-system-overview.md §7.2 |
| 32 | EXPLOIT | Define strategy/execution boundary | COMPLETED | 🤖 | Defined in v1.3-system-overview.md §6.3 |
| 33 | EXPLOIT | Document hybrid task subtypes in field guide | COMPLETED | 🤖 | In field guide + v1.3-enforcement-rules.md |
| 37 | EXPLORE | v1.3 system overview document | COMPLETED | 🤖 | `v1.3-system-overview.md` exists with 11 sections + 4 appendices |
| 38 | EXPLORE | Process leak vulnerability audit (10 vulnerabilities) | COMPLETED | 🤖 | `v1.3-vulnerability-audit.md` — 10 failure modes + enforcement specs |
| 39 | EXPLORE | Cron map audit (24→10 consolidation) | COMPLETED | 🤖 | `v1.3-cron-registry.md` — all 24 mapped, classified, consolidated |
| 40 | EXPLORE | Enforcement rules audit (AGENTS.md/SOUL.md gaps) | COMPLETED | 🤖 | `v1.3-enforcement-rules.md` — 5 new sections, 4 mods, SOUL.md additions |
| 41 | EXPLOIT | Add cron classification (system/domain) to system overview + cron registry | COMPLETED | 🤖 | §11 has classification table + cron registry has Scope + Model Tier on all 24 |

### Phase 2 — Enforcement Rules & Infrastructure [CURRENT]
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 42 | EXPLOIT | Implement enforcement rules into AGENTS.md | COMPLETED | 🤖 | Validated: 10/10 checks pass. Goal Creation Protocol, Goal Linkage (6b), Hybrid Subtypes (3c), Strategy/Execution Boundary, Morning Briefing, Weekly Review, Model Tiers, v1.3 ref. 429 lines / 21KB. |
| 43 | EXPLOIT | Implement enforcement additions to SOUL.md | COMPLETED | 🤖 | SOUL.md has: System Discipline section + BPMN formalisation north star |
| 46 | EXPLOIT | Add model tier system to system overview + AGENTS.md | COMPLETED | 🤖 | System overview §11.2 + AGENTS.md define 3 tiers with assignment rules |
| 47 | EXPLOIT | Create cron definition template | CAPTURED | 🤖 | `task-system/cron-template.md` exists with: name, scope, model tier, schedule, trigger, inputs, outputs, output location, constraints, tools needed, validation, error handling, linked OpenClaw cron ID, BPMN notation |
| 48 | EXPLOIT | Update system overview — cron output locations, discovery, cross-referencing | CAPTURED | 🤖 | §11 documents: where cron outputs live (`memory/cron-outputs/[name]/YYYY-MM-DD.md`), how downstream processes find outputs, how to discover crons (links to registry) |
| 49 | EXPLOIT | Add one-line descriptions to every cron in system overview + cron registry | CAPTURED | 🤖 | Every cron entry has a one-line description explaining what it means in plain English |
| 50 | EXPLOIT | Add BPMN formalisation north star to SOUL.md + AGENTS.md | CAPTURED | 🤖 | Both files state: "Every process must have explicit trigger, inputs, activities, decision gateways, outputs, error boundaries. Build with DAG portability in mind." |

### Phase 3 — Error Infrastructure [CAPTURED]
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 51 | EXPLOIT | Design centralised error handling file structure | CAPTURED | 🤖 | `task-system/error-handling/README.md` exists with: directory structure, error categories (cron / tool / global infra / domain-specific), how to add new error types, how agents find resolution procedures. Referenced in SOUL.md + AGENTS.md |
| 52 | EXPLOIT | Create error playbook — cron errors | CAPTURED | 🤖 | `task-system/error-handling/cron-errors.md` exists with known cron error patterns → resolution procedures |
| 53 | EXPLOIT | Create error playbook — tool errors | CAPTURED | 🤖 | `task-system/error-handling/tool-errors.md` exists with known tool error patterns (Expandi API, H1 sync, browser, etc.) |
| 54 | EXPLOIT | Create error playbook — global infrastructure errors | CAPTURED | 🤖 | `task-system/error-handling/infra-errors.md` exists with: OpenClaw config, model fallback, auth failures, gateway restart procedures |
| 55 | EXPLOIT | Add error handling protocol to AGENTS.md | CAPTURED | 🤖 | AGENTS.md has: "On error → check category-specific playbook in error-handling/ → if no resolution → check all files in error-handling/ → if still unknown → log structured error + alert Jamie" |
| 56 | EXPLOIT | Add error handling section to system overview | CAPTURED | 🤖 | System overview has §12 Error Handling with: file structure, escalation procedure, structured error log format |
| 57 | EXPLOIT | Create structured error log template | CAPTURED | 🤖 | `memory/error-log/YYYY-MM-DD.md` template with: timestamp, cron/process, phase, error, impact, resolution attempted, outcome, playbook entry created? |

### Phase 4 — Build & Deploy 10 Crons [CAPTURED]
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 58 | EXPLOIT | Build SYSTEM-HEALTH cron (3x daily: 06:00, 12:00, 22:30, Flash) | CAPTURED | 🤖 | Cron exists in OpenClaw, fires 3x, checks all other crons fired, reports failures, writes output to `memory/cron-outputs/system-health/` |
| 59 | EXPLOIT | Rebuild MORNING-BRIEFING cron (07:00, Sonnet) | CAPTURED | 🤖 | Cron exists with: 3 buckets, traffic lights, threshold scan, staleness check, stale tasks, outreach queue section. Sequential execution. Error handling per Phase 3. |
| 60 | EXPLOIT | Confirm MIDDAY-CHECK cron (13:00, Sonnet) | CAPTURED | 🤖 | Cron exists with correct model + error handling |
| 61 | EXPLOIT | Rebuild EVENING-BLOCK cron (21:00, Sonnet) | CAPTURED | 🤖 | Cron exists merging: daily wrap + completion review + domain metrics + tomorrow prep. Sequential. Error handling. |
| 62 | EXPLOIT | Build DAILY-INTEGRITY cron (22:00, Flash) | CAPTURED | 🤖 | Cron exists with 6 sequential checks: task validation, completion audit, KPI collection, registry sync, maturity scan, intake scan. Error handling per check. Output to `memory/cron-outputs/daily-integrity/` |
| 34 | EXPLOIT | Build WEEKLY-REVIEW-PREP cron (Sun 12:00, Sonnet) | CAPTURED | 🤖 | Cron exists with 6 sections: KPI rollup, domain report, foundation check, orphan scan, decision log review, bottleneck analysis. Output to `memory/cron-outputs/weekly-review-prep/` |
| 35 | EXPLOIT | Build MONTHLY-GOAL-REVIEW cron (1st of month, Sonnet) | CAPTURED | 🤖 | Cron exists with monthly review checklist. Output to `memory/cron-outputs/monthly-goal-review/` |
| 63 | EXPLOIT | Build QUARTERLY-ENV cron (1st of quarter, Flash) | CAPTURED | 🤖 | Cron exists with environmental scan checklist trigger |
| 64 | EXPLOIT | Confirm domain crons (EXPANDI-HEALTH, SYNC-EXPANDI-H1) on Flash | CAPTURED | 🤖 | Both crons confirmed on Flash with error handling |
| 65 | EXPLOIT | Delete expired/redundant crons | CAPTURED | 🤖 | EXPANDI-AUTOSEND deleted. Any crons superseded by consolidation removed. OpenClaw cron list matches registry exactly. |
| 11 | EXPLOIT | Build CLAWD-004 scan script (v1.3 compliance) | CAPTURED | 🤖 | `scripts/task-scan.js` checks v1.3 fields + goal linkage + ⚠️ REVIEW flags |

### Phase 5 — Create GOAL-001 & Reformat Tasks [CAPTURED]
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 66 | EXPLOIT | Create GOAL-001 (£5k/month profit) | CAPTURED | 🔄 | `~/Master/goals/GOAL-001.md` exists with: all 8 foundations assessed, sub-goals, mechanism chains with ratios, paths with MVP, threshold gates, system stop criteria |
| 36 | EXPLOIT | Reformat all tasks to v1.3 | CAPTURED | 🤖 | All task files have Goal field, Location field, Decision Log section |
| 67 | EXPLOIT | Add Location field to all existing task files | CAPTURED | 🤖 | All task files have Location: 🏠/📍/🔄 |
| 68 | EXPLOIT | Package worked example for MyOS task_os | CAPTURED | 🔄 | Set of files (goal + tasks + cron definitions + process definitions) that Claude Code can use to build task_os UI |

### Phase 6 — BPMN Formalisation [CAPTURED]
Express every process as formal BPMN notation. Validates process design — reveals loops, missing gateways, unclear branching. Must complete before DAG encoding.
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 69 | EXPLORE | Define BPMN notation standard for task system processes | CAPTURED | 🤖 | `task-system/bpmn-standard.md` exists with: notation format, required elements (trigger event, activities, decision gateways, error boundary events, output events, data objects), examples |
| 70 | EXPLOIT | Convert all system overview processes (§4-§7) to BPMN notation | CAPTURED | 🤖 | Every process in system overview has BPMN-ready definition with: trigger → activities → gateways → outputs → error boundaries |
| 71 | EXPLOIT | Convert all 10 cron definitions to BPMN notation | CAPTURED | 🤖 | Every cron in registry has BPMN process definition alongside the operational prompt |
| 72 | EXPLOIT | Convert error handling escalation to BPMN notation | CAPTURED | 🤖 | Error handling flow expressed as BPMN with decision gateways at each escalation step |
| 73 | EXPLOIT | Validate BPMN completeness — every process has explicit nodes, edges, gateways, no prose-only steps | CAPTURED | 🤖 | Validation report confirms all BPMN definitions are complete. Any design issues (loops, missing branches) fixed before Phase 7. |

### Phase 7 — DAG Encoding & MyOS Portability [CAPTURED]
Take validated BPMN definitions and encode as machine-readable directed acyclic graphs. Depends on Phase 6 completion — cannot encode processes that haven't been formalised and validated first.
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 74 | EXPLOIT | Define DAG schema for MyOS task_os consumption | CAPTURED | 🔄 | JSON/YAML schema that represents process flow as nodes + edges with execution semantics, consumable by Claude Code |
| 75 | EXPLOIT | Encode all BPMN process definitions as DAG | CAPTURED | 🤖 | Every BPMN definition from Phase 6 encoded in DAG schema. Machine-readable. No prose. |
| 76 | EXPLOIT | Encode all cron BPMN definitions as DAG | CAPTURED | 🤖 | Every cron process from Phase 6 encoded in DAG schema |
| 77 | EXPLOIT | Encode error handling BPMN as DAG | CAPTURED | 🤖 | Error escalation flow encoded in DAG schema |
| 78 | EXPLOIT | Validate DAG portability — can a runtime engine execute these? | CAPTURED | 🤖 | Script or manual validation: every DAG has explicit nodes + edges, all decision branches defined, no orphan nodes, execution order deterministic |
| 79 | EXPLOIT | Package complete DAG set for MyOS task_os handoff | CAPTURED | 🔄 | Directory of DAG files + schema definition + documentation that Claude Code can consume to build task_os execution engine |

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
