# BC-CALL-NOTES — Sales Call Notes Template

> **Summary:** Create a structured sales call notes template that maps to SPIN stages. Used DURING the call to systematically capture answers and AFTER the call to log outcomes and next steps.

**Domain:** boss/sales
**Priority:** 🔴 CRITICAL
**Status:** CAPTURED
**Type:** EXPLOIT
**Cat:** 🔴 A-S (revenue-critical)
**Created:** 2026-02-11
**Depends on:** BC-PRECALL-PREP (call plan), BC-OFFER-V1 (offer document)

## Win State

A single template that Jamie uses during every sales call. Pre-populated with the call plan (from BC-PRECALL-PREP), with blank fields to fill in during the call. After the call, it becomes the permanent record of what was discussed and what happens next.

## Template Structure

### Header
- Lead name, company, role
- Date/time of call
- How they found us (which campaign/intro)
- Call number (1st, 2nd, follow-up)

### RAPPORT NOTES
Pre-filled from call plan. Update during call:
- Personal context discovered: ___
- Shared interests/connections: ___
- Vibe/energy level: ___
- Communication style notes: ___

### S — SITUATION (captured during call)
| Question | Pre-call intel | What they said |
|----------|---------------|----------------|
| Business/role | [pre-filled] | ___ |
| Daily routine/schedule | [pre-filled if known] | ___ |
| Current approach to health/performance | [pre-filled if known] | ___ |
| What tools/systems do they use? | [pre-filled if known] | ___ |
| Any diagnosis/medication? | [pre-filled if known] | ___ |

### P — PROBLEM (captured during call)
| Problem area | Suspected (pre-call) | Confirmed? | Their words |
|-------------|---------------------|-----------|-------------|
| Energy/fatigue | [from H1 tags] | Y/N | "_______" |
| Focus/attention | [from H1 tags] | Y/N | "_______" |
| Consistency/habits | [from H1 tags] | Y/N | "_______" |
| Burnout/stress | [from H1 tags] | Y/N | "_______" |
| Other: ___ | | | "_______" |

**Key problem in their own words:** ___

### I — IMPLICATION (captured during call)
| Question | Their answer |
|----------|-------------|
| Impact on business/revenue | ___ |
| Impact on personal life/health | ___ |
| What have they tried before? | ___ |
| Why didn't it work? | ___ |
| What happens if nothing changes? | ___ |
| How long has this been going on? | ___ |
| Specific example of the problem in action? | ___ |

**Cost of inaction (in their words):** ___

### N — NEED-PAYOFF (captured during call)
| Question | Their answer |
|----------|-------------|
| Do they want to fix this? | Y/N |
| Is it a priority right now? | Y/N — rank: ___/10 |
| Where does it sit vs other priorities? | ___ |
| Is this the right time? | Y/N — why/why not: ___ |
| What would "fixed" look like? | ___ |
| What would solving this be worth? | ___ |
| What do they need in a solution? | ___ |
| When would they want to start? | ___ |
| What format/structure works for them? | ___ |

### OFFER PRESENTED
- Which version of the offer? [reference BC-OFFER-V1]
- Price quoted: ___
- Their reaction: ___
- Objections raised: ___
- How objections were handled: ___

### OUTCOME
- [ ] Closed — start date: ___
- [ ] Follow-up needed — date: ___, reason: ___
- [ ] Not right now — reason: ___, revisit: ___
- [ ] Not a fit — reason: ___

### NEXT STEPS
- [ ] ___ by [date]
- [ ] ___ by [date]
- [ ] ___ by [date]

### POST-CALL NOTES
- What went well: ___
- What to improve: ___
- Key insight/learning: ___
- Update H1 with: ___

## How It Works With Pre-Call Prep

1. **Call booked** → BC-PRECALL-PREP runs → generates call plan
2. **Call plan** auto-populates the pre-call columns in this template
3. **During call** → Jamie fills in "Their answer" / "What they said" columns
4. **After call** → Jamie completes outcome + next steps
5. **Rich** updates H1 with call outcome, next action date, status

## Storage

- Call notes saved to: `calls/YYYY-MM-DD-[lead-name].md`
- Summary pushed to H1 columns: callBooked, attended, offer, closed won/lost, status, nextActionDate

## Sub-Tasks

| # | Task | Status |
|---|------|--------|
| 1 | Create `reference/call-notes-template.md` | CAPTURED |
| 2 | Create `reference/call-plan-template.md` (shared with BC-PRECALL-PREP) | CAPTURED |
| 3 | Build script to auto-generate pre-populated template from H1 data | CAPTURED |
| 4 | Test with mock call | CAPTURED |

## References

- BC-PRECALL-PREP — generates the call plan that pre-fills this template
- BC-OFFER-V1 — offer details referenced during the call
- BOSS-SALES — overall sales workflow

## Decision Log

- 2026-02-11: Task created. SPIN framework mapped to both pre-call plan (what we know + questions) and in-call notes (what they say). Template must capture their exact words for problems/implications — these become case study material and inform future outreach messaging.
