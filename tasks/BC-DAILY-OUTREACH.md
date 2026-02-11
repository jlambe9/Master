# BC-DAILY-OUTREACH — Morning Outreach Priority Block

> **Summary:** Repeatable daily task that presents all outreach actions needed each morning, in priority order. Ensures intros, FUs, replies, and pipeline hygiene happen FIRST before anything else.

**Domain:** boss/lead-gen
**Priority:** 🔴 CRITICAL (daily recurring)
**Status:** CAPTURED
**Type:** EXPLOIT
**Cat:** 🔴 A-S (revenue-critical)
**Created:** 2026-02-11

## Win State

Every morning, Jamie receives a prioritised action list via Telegram. Each item is actionable immediately (copy-paste ready or one-tap approve). Morning outreach block completes before any other work begins.

## When

**Daily at 08:00 GMT** (during cardio — mobile tasks via Telegram)
Cron fires → Rich runs checks → outputs action list to Telegram

## Morning Outreach Checklist (priority order)

### 1. 🔴 REPLY TO RESPONSES
- Check H1 for any leads that replied (column T = replied)
- Check LinkedIn inbox for new messages from connections
- These are the HOTTEST leads — someone engaged, respond NOW
- Output: each response with context + suggested reply

### 2. 🟠 SEND REVIEWED INTROS
- Pull all intros where: reviewed ✅ + passed ✅ + introSent = empty
- Output: count ready to send, names, one-tap link to their LinkedIn profile
- Jamie copies intro from H1 → sends via LinkedIn DM
- After sending: Rich updates introSent date in H1

### 3. 🟡 REVIEW NEW INTROS
- Pull intros written overnight (draft_message exists + aiNotes exists + reviewed = empty)
- Output via mobile-intro-review skill (separate messages, hook + transition only)
- Jamie reviews/edits → Rich updates H1

### 4. 🟡 FOLLOW-UPS & GHOSTS
- Check H1 for leads where intro was sent but no reply within X days:
  - **FU1** (3 days after intro): Pull leads needing first follow-up
  - **FU2** (5 days after FU1): Pull leads needing second follow-up
  - **Ghost message** (5 days after FU2): Final "break-up" message
- Output: each FU needed with suggested message + context
- After Jamie approves: Rich logs send date in H1

### 5. 🟢 CHECK NEW ACCEPTS
- Run detect-new-connections to find any new CR accepts since yesterday
- For new accepts: trigger intro writing pipeline (PB data → competitor screen → write → aiNotes)
- Output: "X new accepts found, intros being written — will appear in tomorrow's review"

### 6. 🟢 PIPELINE HEALTH
- Run `node scripts/expandi-status.js` — CRs on target?
- Any Expandi errors/restrictions?
- Queue status — leads remaining?
- Summary: "Pipeline healthy" or specific alerts

### 7. ⚪ LOG & REPORT
- Update H1 with all actions taken
- Log to `memory/YYYY-MM-DD.md`
- Quick stats: intros sent today, FUs sent, replies received, calls booked

## Output Format (Telegram)

```
☀️ Morning Outreach — [DATE]

🔴 REPLIES (X new)
[Reply details if any, or "None — all clear"]

🟠 READY TO SEND (X intros)
[Names + LinkedIn profile links]

🟡 NEW INTROS TO REVIEW (X)
[Sent as separate messages via mobile-intro-review skill]

🟡 FOLLOW-UPS DUE (X)
[FU details with suggested messages]

🟢 NEW ACCEPTS: X
[Being processed — intros ready by tomorrow]

🟢 PIPELINE: [healthy/warning]
[CRs: X today, target: 100]
```

## What Rich Prepares BEFORE 08:00

Rich should run these checks at 07:30 so everything is ready when Jamie starts cardio:
1. Detect new connections
2. Check for replies in H1
3. Calculate FU/ghost due dates
4. Compile ready-to-send list
5. Check Expandi health
6. Format and send the morning briefing at 08:00

## References

- `skills/mobile-intro-review/SKILL.md` — How to present intros for review
- `skills/detect-new-connections/SKILL.md` — How to find new accepts
- `reference/intro-edit-patterns.md` — Jamie's editing preferences
- `reference/competitor-detection-criteria.md` — Screening rules

## Decision Log

- 2026-02-11: Task created. Jamie wants this as a repeatable daily block to ensure outreach actions happen first every morning during cardio.
