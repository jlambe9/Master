# BOSS-ONBOARD — Define Client Onboarding Process

> **Summary:** Figure out what happens between "client pays" and "first coaching session." No process exists yet.

**Domain:** boss/product
**Priority:** 🔴 CRITICAL
**Status:** CAPTURED
**Type:** EXPLORE
**Cat:** 🔴 A-S
**Owner:** ❓ Undefined
**Next Action:** Map ideal client journey from payment to first session (subtask 1)
**Created:** 2026-02-10
**Pipeline:** v1.1

## Win State
Documented onboarding process: payment → first session. Steps, tools, templates, timeline. Time from payment to first session <48hrs. Tested with mock run-through.

## Steps
| # | Input | Action | Output |
|---|-------|--------|--------|
| 1 | Product design (`boss/product.md`) | Map ideal client journey | Journey map document |
| 2 | Journey map | Create welcome email/pack template | Welcome materials |
| 3 | Scheduling needs | Set up scheduling for initial assessment | Calendly or equivalent |
| 4 | Assessment tools (PSS-10, PANAS, BPS) | Create baseline assessment protocol | Operational assessment flow |
| 5 | All above | Test with mock client run-through | Validated process |

## Subtasks
| # | Type | Task | Status | Owner | Notes |
|---|------|------|--------|-------|-------|
| 1 | EXPLORE | Map ideal client journey | CAPTURED | ❓ | |
| 2 | EXPLOIT | Create welcome email/pack | CAPTURED | 🤖 Rich | Template |
| 3 | EXPLOIT | Set up scheduling | CAPTURED | 🤖 Rich | Calendly? |
| 4 | EXPLOIT | Create baseline assessment protocol | CAPTURED | 🔄 | Designed in product.md, not operational |
| 5 | EXPLOIT | Mock client run-through | CAPTURED | 🔄 | |

## Dependencies / Links
- **Upstream:** BC-OFFER-V1 (what are we onboarding them into?), BOSS-GDPR (legal docs part of onboarding), BC-CLIENT-APP (bot setup is part of onboarding)
- **Downstream:** First paying client experience, client retention
- **Related:** `boss/product.md` (program design), assessment tools (PSS-10, PANAS)
- **Tools:** Payment system (TBD), Calendly?, assessment tools

## Notes
- Pre-revenue chicken-and-egg: must exist before first sale but no clients to test with
- Assessment tools designed in product.md but not operationalised

## Decision Log
- 2026-02-10: Created. Must exist before first paying client.

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🔴 A-S | |
| Failure point | Goal clarity (what does onboarding include?) | |
| Duration | 4h ⚠️ REVIEW | |
| Intervention | Start with journey map, not full process | |
| Effectiveness | | |

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | High | No process exists, many decisions |
| Procedure specification | Open | Needs designing from scratch |
| Procedure complexity | Complex | Multiple tools, templates, flows |
| Temporal delay | Days | Design → build → test |
| Error cost | Moderate | Bad onboarding → bad first impression |
| Reward magnitude | Med | Enables clients, not direct revenue |
| Reward probability | Likely | Will produce a process |
| Value density per unit | Med | Design phases exploratory |
| Feedback latency | Very delayed | Validated by first real client |
| Process legibility | Partial | Big design task |
| Model maturity | Novel | First time |
| State-tracking load | Med | Multiple components |

### 0B: Channel Requirements
- **Input route:** Design thinking (Gc,Gf) → strong
- **Processing route:** Process design (Gf,Gwm) → strong
- **Output route:** Documentation (Gc,Grw) → strong
- **Channel flexible:** Y
- **Mismatch flags:** None

### 0C: Affective Load
| Dimension | Present | Intensity |
|-----------|---------|-----------|
| Interpersonal risk | N | — |
| Status challenge | N | — |
| Exposure / visibility | Y | Low — internal process |
| Uncertain return | Y | Med — will it work? |
| Confrontation potential | N | — |
| Identity-relevant outcome | Y | Med — "am I professional enough?" |

### Layer 3 Computation
- **Epistemic value:** High (novel design)
- **Pragmatic value:** Medium
- **Effort cost:** High
- **Threat:** Medium
- **Dominant signal:** → 🔴 A-S (identity + uncertain return, but structurable)

### Predicted Failure Point
- **Stage:** Goal clarity
- **Cause:** Too many unknowns, no urgency without clients
- **Auto-intervention:** Surface when first call booked as deadline trigger

### Intervention Stack (if B/A)
- **Drivers:** Identity relevance, uncertain return
- **Stack:** Minimum viable onboarding (email + Calendly + assessment), iterate after first client
- **Confidence:** UNTESTED
- **Conflicts checked:** N

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-10 | Initial creation | Rich |
| 1.1 | 2026-02-21 | Reformatted to v1.1 template | Atlas |
