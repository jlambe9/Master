# BC-CALL-NOTES — Sales Call Notes Template (Sandler Framework)

> **Summary:** Structured template used DURING sales calls to systematically capture answers at each Sandler stage. Pre-populated from BC-PRECALL-PREP, filled in live, becomes permanent record.

**Domain:** boss/sales
**Priority:** 🔴 CRITICAL
**Status:** CAPTURED
**Type:** EXPLOIT
**Cat:** 🔴 A-S (revenue-critical)
**Created:** 2026-02-11
**Depends on:** BC-PRECALL-PREP (call plan), BC-OFFER-V1 (offer document)

## Win State

A single template pre-filled with known intel (from call plan). Jamie fills in "what they said" during the call. After the call, it's the permanent record + triggers next actions in H1.

## Template Structure

### Header
- Lead name, company, role
- Date/time of call
- How they found us (campaign, intro hook)
- Call number (discovery, follow-up, close)

---

### STAGE 1: BONDING & RAPPORT
| Pre-call intel | Notes from call |
|---------------|-----------------|
| [shared context] | ___ |
| [personal hooks] | ___ |
| Communication style: | ___ |
| Vibe/energy: | ___ |

---

### STAGE 2: UP-FRONT CONTRACT
- Agenda set? Y/N
- Their expectations: ___
- Time agreed: ___
- What they want from the call: ___

---

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

---

### STAGE 4: BUDGET
| Question | Their answer |
|----------|-------------|
| Have you set aside resources for this? | ___ |
| What investment would you be comfortable with? | ___ |
| Is budget a constraint or is it about finding the right solution? | ___ |
| Any signals about capacity: | ___ |

**Budget qualified?** Y/N — Notes: ___

---

### STAGE 5: DECISION
| Question | Their answer |
|----------|-------------|
| Who else is involved in this decision? | ___ |
| What does your decision process look like? | ___ |
| Is this a priority right now? Rank /10: | ___/10 |
| Where does it sit vs other priorities? | ___ |
| Is this the right time? Why/why not? | ___ |
| What would you need to see/know to decide? | ___ |
| When would you want to get started? | ___ |
| What structure/format works best for you? | ___ |

**Decision qualified?** Y/N — Notes: ___

---

### STAGE 6: FULFILLMENT (only if pain, budget, decision qualified)
- Offer version presented: [reference BC-OFFER-V1]
- Pain points mapped to solution:
  - Pain: ___ → Our solution: ___
  - Pain: ___ → Our solution: ___
- Price quoted: ___
- Their reaction: ___
- Objections raised: ___
- How handled: ___

---

### STAGE 7: POST-SELL
- Decision confirmed? Y/N
- Start date agreed: ___
- "What could cause you to change your mind?": ___
- Next steps:
  - [ ] ___ by [date]
  - [ ] ___ by [date]
  - [ ] ___ by [date]

---

### OUTCOME
- [ ] **Closed** — start date: ___, payment: ___
- [ ] **Follow-up needed** — date: ___, what's needed: ___
- [ ] **Not right now** — reason: ___, revisit when: ___
- [ ] **Not a fit** — reason: ___

### POST-CALL REFLECTION
- What went well: ___
- What to improve: ___
- Key insight/learning: ___
- Which Sandler stage did we get stuck at? ___
- What do we need to prepare for next call? ___

## How It Works

1. **Call booked** → BC-PRECALL-PREP runs → generates call plan
2. **Call plan** auto-populates the pre-call intel columns in this template
3. **During call** → Jamie fills in "their answer" / "exact words" columns
4. **After call** → Jamie completes outcome + post-call reflection
5. **Rich** updates H1 with: call outcome, next action date, status, pain notes

## Storage

- Call notes: `calls/YYYY-MM-DD-[lead-name].md`
- Summary → H1 columns: callBooked, attended, offer, closed won/lost, status, nextActionDate

## Key Sandler Principles to Remember

- **Don't present before qualifying.** Pain → Budget → Decision → THEN Fulfillment.
- **Capture their exact words.** Their language becomes your selling language.
- **It's OK to walk away.** If pain isn't real, budget isn't there, or they can't decide — that's a qualified "no." Better than a wasted proposal.
- **The buyer convinces the seller.** You're not pushing — you're discovering if there's a fit.

## References

- BC-PRECALL-PREP — generates the call plan
- BC-OFFER-V1 — offer details for Fulfillment stage
- BOSS-SALES — overall sales workflow

## Decision Log

- 2026-02-11: Task created. Sandler framework with 7 stages. Template captures exact words at each stage. Key: don't present solution until pain, budget, and decision are all qualified.
