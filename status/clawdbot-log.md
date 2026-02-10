# ClawdBot Log

## 2026-02-10 15:30

### BC-052 Updates
- Created MVP intro-writing-spec at `~/clawd/reference/intro-writing-spec.md` (v1.0)
- Consolidated template, personalization rules, real good/bad examples, validation criteria into single file
- Updated `~/clawd/processes/write-intro-messages.md` — now references MVP spec, correct column (J), includes daily process

### Intro Writing — Daily Repeat Task
- **Type:** Daily repeat, runs via cron at 21:30 ("Daily Intro Catch-up")
- **Process:** `~/clawd/processes/write-intro-messages.md`
- **Find leads:** `node scripts/check-intro-backlog.js --json` → returns accepted connections with no draft
- **Write intros:** Using `reference/intro-writing-spec.md` (v3 template + layered personalization)
- **Output:** H1 column J only
- **Skip rule:** If insufficient profile data, write SKIP not a generic intro

### STATUS.md suggested updates
- BC-052: Stage → EXPLOIT, next action = "Jamie review MVP spec, then daily execution"
- Add "Write intros for new connections" as daily repeat task in Active
