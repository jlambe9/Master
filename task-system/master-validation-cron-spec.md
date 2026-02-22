# Master Validation Cron — Spec

## Purpose

Single cron that validates the OUTPUT of all other crons against defined validation criteria. Not a health check (that's system-health). This validates that crons which fired and claimed success actually produced correct, complete output.

## Why This Exists

The system health cron checks "did it fire?" This cron checks "did it fire AND produce correct output?" These are different questions. A cron can fire successfully, produce garbage, and system-health would report it as healthy.

Proven by: 2026-02-23 system health false alarm — cron fired, produced output, but the output was wrong (false critical diagnosis, bad recommendation, no self-healing attempted).

## Trigger

Fires **once daily at 23:00** (after all daily crons have fired: morning 07:00, midday 13:00, evening 21:00, integrity 22:00). Also checks most recent output of recurring crons (expandi-health, sync-expandi-h1).

## What It Validates

For each cron that produced output today, check its output against defined validation criteria.

### Validation Criteria Per Cron

**SYSTEM-HEALTH** (`memory/cron-outputs/system-health/YYYY-MM-DD-*.md`)
- File exists for today (at least one, up to 3)
- Contains "Summary" section with cron count
- Contains status table with all 10 crons listed
- Does NOT contain "critical" or "restart gateway" unless self-healing section documents what was tried
- If it recommended action to Jamie: was the self-validation step documented? (Step 4 in prompt)

**MORNING-BRIEFING** (output delivered to Jamie via main session)
- Check: did the main session produce a morning briefing message today? (Look for morning-briefing output or check memory/cron-outputs/morning-briefing/)
- If output file exists: contains sections for Context, Must Do, Should Do, Could Do
- Traffic light emojis present (🔴/🟡/🟢 for priority, ✅/⚠️/🔴/❓ for strategy)
- If goal files don't exist: output says "No goals defined" (not a hallucinated goal summary)

**MIDDAY-CHECK** (output delivered to Jamie via main session)
- Lightweight: just check it fired. Output is conversational, hard to validate structurally.
- Flag if: output is >500 words (should be 2-4 lines per spec)

**EVENING-BLOCK** (`memory/cron-outputs/evening-block/YYYY-MM-DD.md`)
- File exists for today
- Contains 4 sections: Daily Wrap, Completion Review, Domain Metrics, Tomorrow Prep
- If any task was marked COMPLETED today: Completion Review section mentions it and verifies outputs

**DAILY-INTEGRITY** (`memory/cron-outputs/daily-integrity/YYYY-MM-DD.md`)
- File exists for today
- Contains all 6 check sections (even if individual checks errored)
- If a check errored: error is logged in that section (not silently swallowed)
- Registry sync check: if it reported sync needed, verify ~/clawd/TASK-REGISTRY.md was actually updated

**WEEKLY-REVIEW-PREP** (`memory/cron-outputs/weekly-review-prep/YYYY-MM-DD.md`)
- Only check if today is Sunday or Monday (gives 1 day grace)
- If Sunday: file exists for this week
- Contains 6 sections: KPI Rollup, Domain Report, Foundation Check, Orphan Scan, Decision Log Review, Bottleneck Analysis

**MONTHLY-GOAL-REVIEW** (`memory/cron-outputs/monthly-goal-review/YYYY-MM.md`)
- Only check on 1st-3rd of month (grace period)
- File exists for this month

**QUARTERLY-ENV** (`memory/cron-outputs/quarterly-env/YYYY-QN.md`)
- Only check on 1st-3rd of Jan/Apr/Jul/Oct
- File exists for this quarter

**EXPANDI-HEALTH** (`memory/cron-outputs/expandi-health/YYYY-MM-DD-*.md`)
- At least one file exists for today (runs every 2h during 06-22)
- File is not empty
- Does not contain recommendations without evidence (same false-alarm pattern as system-health)

**SYNC-EXPANDI-H1** (`memory/cron-outputs/sync-expandi-h1/YYYY-MM-DD-*.md`)
- At least one file exists for today (runs every 3h during 06-22)
- File is not empty

## Validation Logic

For each cron:
1. Find today's output file(s) at the expected path
2. If no file and cron was supposed to fire today: FLAG as "no output" (different from "didn't fire" which system-health catches)
3. If file exists: run the structural checks above
4. If structural checks fail: FLAG with specific violation

## Output

Write to `memory/cron-outputs/master-validation/YYYY-MM-DD.md`

Format:
```
# Master Validation — YYYY-MM-DD

## Summary
- Crons validated: N
- ✅ Pass: N
- ⚠️ Structural issues: N
- 🔴 No output (should have fired): N
- ⏭️ Not due today: N

## Results

| Cron | Status | Output Path | Issues |
|------|--------|-------------|--------|
| System Health | ✅ Pass | .../2026-02-23-0600.md | |
| Morning Briefing | ⚠️ Issue | (main session) | Missing traffic lights |
| ... | | | |

## Detail
[For each ⚠️ or 🔴: what was expected, what was found]
```

## Escalation

- 0 issues: write file silently
- 1-2 ⚠️ structural issues: write file silently + log in error-log (might be prompt tuning needed, not urgent)
- Any 🔴 no-output: alert Jamie — a cron that fires but produces nothing is worse than one that doesn't fire (system-health catches the latter)
- 3+ ⚠️ structural issues: alert Jamie — pattern suggests prompts are degrading

## What This Cron Does NOT Do

- Does NOT validate whether the cron's recommendations were correct (that requires domain knowledge)
- Does NOT re-run failed crons (system-health does that via self-healing)
- Does NOT modify cron prompts (that requires human decision)
- Does NOT validate its own output (that would be infinite regression — its output is simple enough that structural correctness = correctness)

## Why Infinite Regression Doesn't Apply

This cron's output is a simple pass/fail table. The validation criteria are: does file exist, does it have the right sections, does it not contain known-bad patterns. These are mechanical checks, not judgment calls. A Flash agent can do them reliably because there's no ambiguity. The problem with the system-health cron was that it required JUDGMENT (is this cron healthy?) — this one requires only OBSERVATION (does this file exist and contain these strings?).

## Model Tier

Flash. This is pure structural validation — no judgment, no reasoning, no recommendations. Just file checks.

## Schedule

`0 23 * * *` (23:00 daily, after all daily crons have fired)

## Error Handling

On error: log to `memory/error-log/YYYY-MM-DD.md`. If the master validation cron itself fails to produce output, system-health will catch it on its next run (it checks all cron output directories).
