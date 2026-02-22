# [TASK-ID] — [Task Name]

> **Summary:** [One line]

**Domain:** [boss/area or domains/area]
**Priority:** [🔴 CRITICAL / 🟡 HIGH / ⚪ MEDIUM]
**Status:** CAPTURED
**Type:** [EXPLORE / EXPLOIT / ADMIN]
**Cat:** [🟢 E / 🟡 B / 🔴 A-S / 🔴 A-I / 🟠 M]
**Owner:** [🤖 Rich / 🔄 Hybrid / 🧑 Jamie / ❓ Undefined]
**Maturity:** [L0-L9]
**Next Action:** [Agent-generated — what happens next]
**Created:** [date]
**Pipeline:** v1.2
**Field Guide:** task-system/task-field-guide.md
**Goal:** [GOAL-ID | PATH-ID | Mechanism Step — e.g. GOAL-001 | PATH-LI | M1: Outreach] *(optional)*

## Dependencies
- **Hard → (can't proceed without):** [task IDs]
- **Soft ~> (improves but not required):** [task IDs]
- **Threshold ⊕ (proceeds when condition met):** [task ID + condition, e.g. "BC-SALES ⊕ ≥10 signups"]
- **Downstream (blocks):** [what can't start until this is done]
- **Domain checklist:** [boss/lead-gen, boss/sales, etc — see task-field-guide.md]

## Win State
[What "done" looks like — specific, observable, output-defined]
**Outputs (completion gate — ALL must exist to mark done):**
1. [Specific deliverable/artifact/state change that proves this is done]
2. [Another one]

## Subtasks
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 1 | | | CAPTURED | | |

## Execution Log
| Date | What Happened | Outcome | Duration | Version |
|------|--------------|---------|----------|---------|

## Decision Log
| Date | Decision | Rationale | Reversible? |
|------|----------|-----------|-------------|
| | | | |

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | | |
| Failure point | | |
| Duration | | |
| Intervention | | |
| Effectiveness | | |

<!-- ============================================ -->
<!-- RTP SECTION — fill when task recurs 2+ times -->
<!-- Once all RTP fields filled → maturity = L6   -->
<!-- ============================================ -->

## Process Version
**Current:** v1.0

## Process Version Stack
| Version | Dates Active | What Changed | Why | Outcome vs Previous |
|---------|-------------|-------------|-----|-------------------|
| v1.0 | [created] - present | Initial process | First documented | — |

## Component Registry
<!-- All data objects, tools, accounts, files that flow through this process -->
| Component | Type | Used In Subtasks | Source | Notes |
|-----------|------|--------------|--------|-------|
| | | | | |

## Automation Requirements
<!-- What would need to exist for Rich to do this E2E autonomously? -->
- **Scripts needed:** [existing or to-build]
- **Access needed:** [APIs, accounts, credentials]
- **Verification method:** [how to confirm output is correct without Jamie]
- **Edge cases to handle:** [known failure modes]
- **Human checkpoints:** [where Jamie MUST be involved, if any]

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | | |
| Procedure specification | | |
| Procedure complexity | | |
| Temporal delay | | |
| Error cost | | |
| Reward magnitude | | |
| Reward probability | | |
| Value density per unit | | |
| Feedback latency | | |
| Process legibility | | |
| Model maturity | | |
| State-tracking load | | |

### 0B: Channel Requirements
- **Input route:** [default] → [Jamie's best route]
- **Processing route:** [default] → [Jamie's best route]
- **Output route:** [default] → [Jamie's best route]
- **Channel flexible:** [Y/N]
- **Mismatch flags:** [CHC capacities required vs Jamie's profile]

### 0C: Affective Load
| Dimension | Present | Intensity |
|-----------|---------|-----------|
| Interpersonal risk | | |
| Status challenge | | |
| Exposure / visibility | | |
| Uncertain return | | |
| Confrontation potential | | |
| Identity-relevant outcome | | |

### Layer 3 Computation
- **Epistemic value:** [score]
- **Pragmatic value:** [score]
- **Effort cost:** [score]
- **Threat:** [score]
- **Dominant signal:** → [E/B/A/M]

### Predicted Failure Point
- **Stage:** [pipeline stage]
- **Cause:** [from failure analysis table]
- **Auto-intervention:** [from pipeline per-stage table]

### Intervention Stack (if B/A)
- **Drivers:** [from 0C]
- **Stack:** [from intervention-drivers.md]
- **Confidence:** [PROVEN/PRELIMINARY/UNTESTED]
- **Conflicts checked:** [Y/N — which]

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | [created] | Initial scoring | [agent] |
