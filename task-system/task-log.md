# Task Log — Accumulated Profiles

*Each task type appears once with execution history. Log file — will grow.*
*New profiles added when first encountered. Execution data appended after each instance.*

## Profile Template

```
### [Task Name]
- **Domain:** [boss/area or domains/area]
- **Created:** [date]
- **Layer 0:** Entropy: [L/M/H] | Spec: [S/P/O] | Complexity: [S/M/C] | Error: [R/M/H]
- **Channel:** Default [X] → Jamie's route [Y] | Flexible: [Y/N]
- **Affective:** [active dimensions]
- **Predicted:** [E/B/A/M] | **Failure point:** [pipeline stage]
- **Intervention:** [initial approach]
- **Est. duration:** [guess]
- **Notes:** [free text]

#### Execution History
| Date | Duration | Cat | Deviation | Friction | Output | Notes |
|------|----------|-----|-----------|----------|--------|-------|
```

## Profiled Tasks

### Write Intro Messages (Daily Repeat)
- **Domain:** boss/lead-gen
- **Created:** 2026-02-10
- **Ref:** BC-052 (spec), BC-063 (execution)
- **Layer 0:** Entropy: M | Spec: S | Complexity: M | Error: M
- **Channel:** Default: Research (LinkedIn profile) → Writing (personalized hook) | Flexible: N
- **Affective:** SEEKING (research is engaging), mild aversion (repetitive once pattern learned)
- **Predicted:** 🟢 E initially → 🟡 B after ~2 weeks | **Failure point:** Initiation (finding time daily)
- **Intervention:** Automated via cron (21:30 daily catch-up), removes initiation barrier
- **Est. duration:** ~5 min/lead (research + write), batch of 5-10 = 30-60 min
- **Spec:** `~/clawd/reference/intro-writing-spec.md`
- **Process:** `~/clawd/processes/write-intro-messages.md`
- **Find leads:** `node scripts/check-intro-backlog.js --json`
- **Output:** H1 column J (draft_message)
- **Notes:** MVP spec consolidated 2026-02-10. Skip if insufficient data — never send generic intros.

#### Execution History
| Date | Duration | Cat | Deviation | Friction | Output | Notes |
|------|----------|-----|-----------|----------|--------|-------|
| 2026-01-28 | ~2h | 🟢 E | None | Low | 27 intros | First batch, manual |
| 2026-02-03 | ~5min | 🟠 M | High | High | 8 intros (all fallback) | Auto-gen failed — no profile data |
