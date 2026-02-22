# CLAWD-004 — Daily Task Template Scan

> **Summary:** Daily automated scan of all task files for v1.1 gaps, missing sections, and maturity blockers. Outputs remediation list.

**Domain:** clawd/ops
**Priority:** 🟡 HIGH
**Status:** CAPTURED
**Type:** EXPLOIT
**Cat:** 🟢 E
**Owner:** 🤖 Rich
**Next Action:** Build scan script (node or shell) that checks each task file against v1.1 template
**Created:** 2026-02-20
**Pipeline:** v1.2

## Win State
Every day at 16:00, Rich scans all task files in ~/Master/tasks/ and:
**Outputs (completion gate — ALL must exist to mark done):**
1. ⚠️ REVIEW — outputs not yet defined
1. Identifies tasks NOT in v1.1 format
2. Identifies missing required sections
3. Identifies maturity gaps
4. Outputs remediation list in priority order
5. Updates TASK-REGISTRY.md with current maturity levels
6. Alerts Jamie only if critical tasks have format gaps

## Subtasks
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 1 | EXPLOIT | Build scan script | CAPTURED | 🤖 Rich | Compare sections present vs required |
| 2 | EXPLOIT | Create 16:00 daily cron | CAPTURED | 🤖 Rich | Isolated session |
| 3 | EXPLOIT | Auto-fix inferrable fields | CAPTURED | 🤖 Rich | Only unambiguous fills |

## Dependencies / Links
- **Upstream:** META-TASK-SYSTEM (v1.1 template must be defined), all task files
- **Downstream:** Task quality maintenance, TASK-REGISTRY.md accuracy
- **Related:** CLAWD-001 (cron reliability)

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🟢 E | |
| Failure point | None (Rich E2E) | |
| Duration | 2h to build | |
| Intervention | None | |
| Effectiveness | | |

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | Low | Clear spec — compare files to template |
| Procedure specification | Specified | Template exists, comparison logic clear |
| Procedure complexity | Moderate | File parsing + gap detection |
| Temporal delay | Immediate | Build and deploy |
| Error cost | Reversible | Bad scan = re-run |
| Reward magnitude | Med | Maintenance quality |
| Reward probability | Guaranteed | Script works or doesn't |
| Value density per unit | High | Automated quality gate |
| Feedback latency | Immediate | See scan output |
| Process legibility | Clear | Script output |
| Model maturity | Familiar | File scanning pattern |
| State-tracking load | Low | Stateless scan |

### 0B: Channel Requirements
- **Input route:** File system (Rich) → no human needed
- **Processing route:** Pattern matching (Rich) → no human needed
- **Output route:** Script + cron → Rich builds
- **Channel flexible:** N/A — Rich autonomous
- **Mismatch flags:** None

### 0C: Affective Load
All dimensions: N / —

### Layer 3 Computation
- **Epistemic value:** Low
- **Pragmatic value:** Medium
- **Effort cost:** Low
- **Threat:** None
- **Dominant signal:** → 🟢 E (pragmatic, Rich-enjoyable build)

### Predicted Failure Point
- **Stage:** None
- **Cause:** N/A
- **Auto-intervention:** N/A

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-20 | Initial creation | Atlas |
| 1.1 | 2026-02-21 | Reformatted to v1.1 template | Atlas |
