# CLAWD-004 — Daily Task Template Scan

> **Summary:** Daily automated scan of all task files to identify missing v1.1 template sections, format gaps, and maturity blockers. Outputs remediation list.

**Domain:** clawd/ops
**Priority:** 🟡 HIGH
**Status:** CAPTURED
**Type:** EXPLOIT
**Cat:** 🤖 🟢 E
**Owner:** 🤖 Rich
**Next Action:** Build scan script + create cron for 16:00 daily
**Created:** 2026-02-20
**Pipeline:** v1.1

## Win State
Every day at 16:00, Rich scans all task files in ~/Master/tasks/ and:
1. Identifies tasks NOT in v1.1 format
2. Identifies missing required sections (win state, steps, owner, Layer 0)
3. Identifies maturity gaps (e.g. has 5+ instances but no automation requirements)
4. Outputs a remediation list: which tasks need what, in priority order
5. Updates TASK-REGISTRY.md with current maturity levels
6. Alerts Jamie only if critical tasks have format gaps

## Subtasks
| # | Type | Task | Status | Owner | Notes |
|---|------|------|--------|-------|-------|
| 1 | EXPLOIT | Build scan script (node or shell) that checks each task file against v1.1 template | CAPTURED | 🤖 | Compare sections present vs required |
| 2 | EXPLOIT | Create cron job — 16:00 daily, isolated session | CAPTURED | 🤖 | Output: remediation list to Jamie via Telegram |
| 3 | EXPLOIT | Auto-fix: for tasks where Rich can infer missing fields, fill them silently | CAPTURED | 🤖 | Only auto-fill what's unambiguous |

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🟢 E | |
| Failure point | None (Rich E2E) | |
| Duration | 2h to build | |
| Intervention | None | |
| Effectiveness | | |
