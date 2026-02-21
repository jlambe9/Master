# BC-CALL-NOTES — Sales Call Notes Template (Sandler Framework)

> **Summary:** Structured template used DURING sales calls to capture answers at each Sandler stage. Pre-populated from BC-PRECALL-PREP, filled live, becomes permanent record.

**Domain:** boss/sales
**Priority:** 🔴 CRITICAL
**Status:** CAPTURED
**Type:** EXPLOIT
**Cat:** 🔴 A-S
**Owner:** 🔄 Hybrid
**Next Action:** Build template file at `reference/call-notes-template.md` from spec below
**Created:** 2026-02-11
**Pipeline:** v1.1

## Win State
A reusable template: pre-filled with known intel (from call plan), Jamie fills in "what they said" during the call. After call = permanent record + triggers next actions in H1.

## Steps
| # | Input | Action | Output |
|---|-------|--------|--------|
| 1 | BC-PRECALL-PREP (call plan) | Auto-populate pre-call intel columns | Pre-filled template |
| 2 | Live call | Jamie fills "their answer" / "exact words" columns | Completed call notes |
| 3 | Completed notes | Jamie fills outcome + post-call reflection | Final record |
| 4 | Final record | Rich updates H1: call outcome, next action, status, pain notes | Updated pipeline |

## Dependencies / Links
- **Upstream:** BC-PRECALL-PREP (generates call plan that populates this), BC-OFFER-V1 (offer details for Fulfillment stage)
- **Downstream:** BOSS-ONBOARD (closed deals trigger onboarding), H1 pipeline updates
- **Related:** BOSS-SALES (overall sales workflow)
- **Storage:** `calls/YYYY-MM-DD-[lead-name].md`, summary → H1 columns

## Template Structure

### Header
- Lead name, company, role, date/time, how found, call number

### STAGE 1: BONDING & RAPPORT
| Pre-call intel | Notes from call |
|---------------|-----------------|
| [shared context] | ___ |
| [personal hooks] | ___ |
| Communication style: | ___ |
| Vibe/energy: | ___ |

### STAGE 2: UP-FRONT CONTRACT
- Agenda set? Y/N
- Their expectations: ___
- Time agreed: ___
- What they want from the call: ___

### STAGE 3: PAIN (The Pain Funnel)

**Level 1 — Surface Pain**
| Question | Their answer (exact words) |
|----------|--------------------------|
| What's going on? / What prompted you? | "_______" |
| Tell me more about that | "_______" |
| Can you be more specific? | "_______" |
| Give me an example | "_______" |

**Level 2 — Business Impact**
| Question | Their answer (exact words) |
|----------|--------------------------|
| How long has this been going on? | "_______" |
| What have you tried to do about it? | "_______" |
| Did that work? Why / why not? | "_______" |
| How much has it cost you? (time/money/opportunity) | "_______" |

**Level 3 — Personal Impact**
| Question | Their answer (exact words) |
|----------|--------------------------|
| How is this affecting you personally? | "_______" |
| How do you feel about that? | "_______" |
| Have you given up trying to fix this? | "_______" |

**Key pain summary (their words):** ___
**Pain level reached:** L1 / L2 / L3

### STAGE 4: BUDGET
| Question | Their answer |
|----------|-------------|
| Have you set aside resources for this? | ___ |
| What investment would you be comfortable with? | ___ |
| Is budget a constraint or about finding the right solution? | ___ |

**Budget qualified?** Y/N

### STAGE 5: DECISION
| Question | Their answer |
|----------|-------------|
| Who else is involved in this decision? | ___ |
| What does your decision process look like? | ___ |
| Is this a priority right now? Rank /10: | ___/10 |
| What would you need to see/know to decide? | ___ |
| When would you want to get started? | ___ |

**Decision qualified?** Y/N

### STAGE 6: FULFILLMENT (only if pain, budget, decision qualified)
- Offer version presented: [reference BC-OFFER-V1]
- Pain points mapped to solution
- Price quoted / reaction / objections / how handled

### STAGE 7: POST-SELL
- Decision confirmed? Y/N
- Start date agreed / Next steps / "What could cause you to change your mind?"

### OUTCOME
- [ ] Closed — start date, payment
- [ ] Follow-up needed — date, what's needed
- [ ] Not right now — reason, revisit when
- [ ] Not a fit — reason

### POST-CALL REFLECTION
- What went well / improve / key insight / stuck Sandler stage / prep for next call

## Key Sandler Principles
- Don't present before qualifying: Pain → Budget → Decision → THEN Fulfillment
- Capture their exact words — their language becomes your selling language
- It's OK to walk away — qualified "no" beats wasted proposal
- The buyer convinces the seller — discovering fit, not pushing

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🔴 A-S | |
| Failure point | Initiation (building template) | |
| Duration | 2h ⚠️ REVIEW | |
| Intervention | Restructure (A-S → template task) | |
| Effectiveness | | |

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | Low | Sandler framework is specified |
| Procedure specification | Specified | Framework + template fully designed above |
| Procedure complexity | Moderate | 7 Sandler stages, multiple fields |
| Temporal delay | Immediate | Build template now |
| Error cost | Moderate | Bad template → missed info in calls |
| Reward magnitude | High | Enables structured sales calls |
| Reward probability | Guaranteed | Template = done |
| Value density per unit | High | Direct sales enablement |
| Feedback latency | Delayed | Quality proven on first real call |
| Process legibility | Clear | Template is visible artifact |
| Model maturity | Novel | First structured sales template |
| State-tracking load | Low | Single template build |

### 0B: Channel Requirements
- **Input route:** Reading Sandler framework (Gc,Grw) → strong
- **Processing route:** Semantic structuring (Gc,Gf) → strong
- **Output route:** Template writing (Gc,Grw) → strong
- **Channel flexible:** Y — Rich drafts, Jamie reviews
- **Mismatch flags:** None

### 0C: Affective Load
| Dimension | Present | Intensity |
|-----------|---------|-----------|
| Interpersonal risk | Y | Low — template, not the call itself |
| Status challenge | N | — |
| Exposure / visibility | N | — |
| Uncertain return | N | — |
| Confrontation potential | N | — |
| Identity-relevant outcome | Y | Low — "am I a real business?" feeling |

### Layer 3 Computation
- **Epistemic value:** Low
- **Pragmatic value:** High
- **Effort cost:** Low (Rich can draft)
- **Threat:** Low (A-S — structurable)
- **Dominant signal:** → 🔴 A-S (mild threat, but restructuring makes it an exploit task)

### Predicted Failure Point
- **Stage:** Initiation
- **Cause:** Competes with outreach priorities
- **Auto-intervention:** Rich drafts template, Jamie reviews — minimal Jamie effort

### Intervention Stack (if B/A)
- **Drivers:** Mild identity relevance
- **Stack:** Rich drafts first (removes blank-page aversion), Jamie reviews (editing vs creating)
- **Confidence:** PRELIMINARY
- **Conflicts checked:** N

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-11 | Initial creation | Rich |
| 1.1 | 2026-02-21 | Reformatted to v1.1 template | Atlas |
