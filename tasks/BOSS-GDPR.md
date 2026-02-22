# BOSS-GDPR — GDPR/Data Handling Policy + Legal Compliance

> **Summary:** Create legal documents needed to operate as a coaching business — privacy policy, terms, client contracts, GDPR compliance. Required before first client.

**Domain:** boss/legal-hr
**Priority:** 🔴 CRITICAL
**Status:** CAPTURED
**Type:** EXPLORE
**Cat:** 🔴 A-S
**Owner:** 🔄 Hybrid
**Next Action:** Rich researches ICO registration requirements (subtask 1)
**Created:** 2026-02-10
**Pipeline:** v1.2

## Win State
GDPR-compliant data handling policy, privacy policy, terms & conditions, and client contract — all drafted and reviewed. ICO registration confirmed or ruled out. Ready before first paying client.
**Outputs (completion gate — ALL must exist to mark done):**
1. Privacy policy drafted and reviewed
2. Terms & conditions drafted and reviewed
3. Client contract/agreement drafted and reviewed
4. ICO registration confirmed or ruled out
5. Internal data handling policy created

## Subtasks
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 1 | EXPLORE | Determine ICO registration requirements | CAPTURED | 🤖 Rich | Research task |
| 2 | EXPLORE | Determine professional indemnity insurance | CAPTURED | 🤖 Rich | Research task |
| 3 | EXPLOIT | Draft privacy policy | CAPTURED | 🤖 Rich | From template |
| 4 | EXPLOIT | Draft terms & conditions | CAPTURED | 🤖 Rich | From template |
| 5 | EXPLOIT | Draft client contract/agreement | CAPTURED | 🤖 Rich → 🧑 Jamie reviews | |
| 6 | EXPLOIT | Create data handling policy (internal) | CAPTURED | 🤖 Rich | |

## Dependencies / Links
- **Upstream:** BC-OFFER-V1 (need to know what we're offering to write contracts), BC-CLIENT-APP (data architecture for GDPR)
- **Downstream:** BOSS-ONBOARD (legal docs are part of onboarding), first paying client (BLOCKER — must exist before)
- **Related:** `boss/legal-hr.md` compliance checklist

## Decision Log
- 2026-02-10: Created. Non-negotiable legal requirement before first client.

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🔴 A-S | |
| Failure point | Planning (when to prioritise vs revenue tasks) | |
| Duration | 6h ⚠️ REVIEW | |
| Intervention | Rich drafts all docs, Jamie reviews | |
| Effectiveness | | |

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | Med | Legal requirements need research |
| Procedure specification | Partial | Templates exist, specifics TBD |
| Procedure complexity | Moderate | 6 documents, some interdependent |
| Temporal delay | Days | Draft → review cycle |
| Error cost | High | Legal non-compliance = risk |
| Reward magnitude | Med | Enables business, no direct revenue |
| Reward probability | Guaranteed | Documents = done |
| Value density per unit | Med | Research phases lower density |
| Feedback latency | Delayed | Validated by use |
| Process legibility | Clear | 6 documents, visible progress |
| Model maturity | Novel | First time doing legal setup |
| State-tracking load | Low | Document checklist |

### 0B: Channel Requirements
- **Input route:** Legal research (Gc,Grw) → Rich handles research
- **Processing route:** Semantic drafting (Gc,Gf) → Rich handles
- **Output route:** Document writing → Rich handles
- **Channel flexible:** Y — Rich researches + drafts, Jamie reviews
- **Mismatch flags:** None

### 0C: Affective Load
| Dimension | Present | Intensity |
|-----------|---------|-----------|
| Interpersonal risk | N | — |
| Status challenge | N | — |
| Exposure / visibility | N | — |
| Uncertain return | N | — |
| Confrontation potential | N | — |
| Identity-relevant outcome | Y | Low — "am I running a real business?" |

### Layer 3 Computation
- **Epistemic value:** Medium (legal research)
- **Pragmatic value:** Medium (enabler, not revenue)
- **Effort cost:** Medium
- **Threat:** Low
- **Dominant signal:** → 🔴 A-S (mild identity, structurable via Rich drafting)

### Predicted Failure Point
- **Stage:** Planning (deprioritised vs revenue tasks)
- **Cause:** No emotional urgency until first client imminent
- **Auto-intervention:** Surface when first call booked — deadline-driven

### Intervention Stack (if B/A)
- **Drivers:** Mild identity relevance
- **Stack:** Rich drafts all, Jamie reviews only. Deadline = first client.
- **Confidence:** UNTESTED
- **Conflicts checked:** N

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-10 | Initial creation | Rich |
| 1.1 | 2026-02-21 | Reformatted to v1.1 template | Atlas |
