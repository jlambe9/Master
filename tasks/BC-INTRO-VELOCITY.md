# BC-INTRO-VELOCITY — Maximum Intro Sending Velocity

> **Summary:** Write, validate, and send intros to ALL current CR accepts. Clear the backlog, then keep pace with new accepts.

**Domain:** boss/lead-gen
**Priority:** 🔴 CRITICAL
**Status:** IN PROGRESS
**Type:** EXPLOIT
**Cat:** 🔴 A-S (revenue-critical)
**Created:** 2026-02-11

## Win State

Every CR-accepted customer lead has a validated intro with aiNotes, reviewed by Jamie, and sent. Zero backlog. New accepts get intros within 24h.

## Current Pipeline Numbers (2026-02-11 16:49)

| Stage | Count | Action |
|-------|-------|--------|
| Ready to send (reviewed) | 8 | Jamie sends |
| Written + edited (Ross, Jonathan) | 2 | Final review → send |
| Nic + Rudy | 2 | Awaiting Jamie's review |
| Written, no context | 13 | ST-1: Validate + add aiNotes |
| CR accepted, no intro (customers) | ~21 | ST-2: Write from scratch |
| CR accepted, no intro (grey area) | ~8 | ST-3: Jamie decides include/exclude |
| CR sent, awaiting accept | 59 | ST-4: Write intros as they accept |

## Sub-Tasks (priority order)

### ST-0: Send the 8 ready intros [JAMIE — NOW]
- These are reviewed and approved. Just copy from H1 column L and send via LinkedIn DM.
- Rows: 3, 4, 5, 14, 15, 22, 26, 27

### ST-1: Validate 13 existing intros + add aiNotes [RICH — NEXT]
- These have draft_message but no aiNotes and haven't been checked against updated process
- Re-validate each against:
  - Competitor screen (updated criteria)
  - Edit patterns from `reference/intro-edit-patterns.md`
  - Add aiNotes for every specific reference
- Then output for Jamie's mobile review
- Estimated: ~30 min sub-agent run

### ST-2: Write intros for 21 accepted customers with no intro [RICH — AFTER ST-1]
- Full write process: PB data → competitor screen → problem tagging → write → aiNotes
- Apply all edit patterns (casual > verbose, ask when uncertain, no uncontextualised refs)
- Then output for Jamie's mobile review
- Estimated: ~45 min sub-agent run

### ST-3: Jamie decides on 8 grey area leads [JAMIE]
- These are ADHD product builders (Saner.AI, Thruday, Neuro, CALMR, etc.)
- Partner, customer, or exclude? Jamie's call per lead.

### ST-4: Real-time monitoring for new accepts [RICH — ONGOING]
- Set up BC-065 (Gmail monitoring) so new accepts trigger immediate intro writing
- Until then: daily check at 21:30 catches stragglers

### ST-5: Send existing 8 ready intros via LinkedIn [RICH — CAN AUTOMATE?]
- Investigate if intros can be sent via Expandi or must be manual LinkedIn DM
- If automatable: build send flow
- If manual: Jamie sends from mobile/desktop

## Dependencies

- **BC-OFFER-V1** improves intro quality (the boilerplate section) but doesn't block sending current intros
- **Competitor screen** ✅ DONE — pipeline is clean
- **Edit patterns** being captured in real-time from Jamie's current review session

## KPIs

- Intros sent per day (target: match CR accept rate, currently ~3-5/day)
- Time from CR accept → intro sent (target: <24h)
- Backlog: zero

## Decision Log

- 2026-02-11: Task created. Current backlog: 8 ready, 13 need validation, 21 need writing. Priority is velocity — clear backlog then maintain pace.
