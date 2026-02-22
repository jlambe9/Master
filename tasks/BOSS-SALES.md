# BOSS-SALES — Sales Call Workflow

> **Summary:** Design the end-to-end process for turning warm leads into paying clients — booking, call script, objection handling, close, onboarding handoff.

**Domain:** boss/sales
**Priority:** 🟡 HIGH
**Status:** CAPTURED
**Type:** EXPLORE
**Cat:** 🔴 A-S
**Owner:** ❓ Undefined
**Next Action:** Consolidate BC-PRECALL-PREP + BC-CALL-NOTES + BC-OFFER-V1 into overall workflow map
**Created:** 2026-02-10
**Pipeline:** v1.2

## Win State
End-to-end sales process: lead books call → Sandler call → close → onboarding handoff. Tested with mock call. Call → sale conversion >25%.
**Outputs (completion gate — ALL must exist to mark done):**
1. ⚠️ REVIEW — outputs not yet defined

## Subtasks
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 1 | EXPLORE | Research coaching sales best practices | CAPTURED | 🤖 Rich | |
| 2 | EXPLOIT | Write call script + objection handling | CAPTURED | 🔄 | BC-PRECALL-PREP covers much of this |
| 3 | EXPLOIT | Set up booking system | CAPTURED | 🤖 Rich | Calendly? |
| 4 | EXPLOIT | Create pricing presentation | CAPTURED | 🔄 | From BC-OFFER-V1 |
| 5 | EXPLOIT | Mock call test | CAPTURED | 🔄 | |

## Dependencies / Links
- **Upstream:** BC-OFFER-V1 (what we're selling), BC-PRECALL-PREP (call prep skill), BC-CALL-NOTES (in-call template)
- **Downstream:** BOSS-ONBOARD (closed deal → onboarding), revenue
- **Related:** Outreach pipeline (need leads first)

## Notes
- Much of this is already covered by BC-PRECALL-PREP, BC-CALL-NOTES, BC-OFFER-V1
- This task is the GLUE connecting those pieces into one workflow

## Decision Log
- 2026-02-10: Created. Blocked by outreach pipeline needing leads first.

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🔴 A-S | |
| Failure point | Planning (no urgency without leads) | |
| Duration | 3h ⚠️ REVIEW | |
| Intervention | Consolidate existing sub-tasks | |
| Effectiveness | | |

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | Med | Framework chosen (Sandler), details TBD |
| Procedure specification | Partial | Sub-tasks exist but not unified |
| Procedure complexity | Complex | Multiple components to integrate |
| Temporal delay | Days | Build + mock test |
| Error cost | Moderate | Bad process → lost sales |
| Reward magnitude | High | Direct revenue enablement |
| Reward probability | Likely | Process will exist |
| Value density per unit | Med | Some assembly work |
| Feedback latency | Very delayed | Validated on real calls |
| Process legibility | Partial | Multiple sub-tasks |
| Model maturity | Novel | First sales process |
| State-tracking load | Med | Multiple components |

### 0B: Channel Requirements
- **Input route:** Reading sub-task outputs (Gc,Grw) → strong
- **Processing route:** Integration/synthesis (Gf,Gwm) → strong
- **Output route:** Workflow documentation → Rich can draft
- **Channel flexible:** Y
- **Mismatch flags:** None

### 0C: Affective Load
| Dimension | Present | Intensity |
|-----------|---------|-----------|
| Interpersonal risk | Y | Med — "I have to sell" |
| Status challenge | N | — |
| Exposure / visibility | Y | Med — sales calls are visible |
| Uncertain return | Y | Med — will calls convert? |
| Confrontation potential | Y | Low — potential rejection |
| Identity-relevant outcome | Y | High — "am I a salesperson?" |

### Layer 3 Computation
- **Epistemic value:** Medium
- **Pragmatic value:** High
- **Effort cost:** Medium
- **Threat:** High (multiple A drivers)
- **Dominant signal:** → 🔴 A-S (high threat but structurable via Sandler framework)

### Predicted Failure Point
- **Stage:** Initiation
- **Cause:** Sales = identity-threatening for Jamie
- **Auto-intervention:** Frame as Sandler process (qualification, not selling), Rich preps everything

### Intervention Stack (if B/A)
- **Drivers:** Interpersonal risk, identity relevance, uncertain return, confrontation
- **Stack:** Preparation script (Sandler), outcome pre-processing, Rich preps all materials, mock call first
- **Confidence:** PRELIMINARY
- **Conflicts checked:** N

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-10 | Initial creation | Rich |
| 1.1 | 2026-02-21 | Reformatted to v1.1 template | Atlas |
