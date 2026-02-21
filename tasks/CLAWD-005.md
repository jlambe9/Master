# CLAWD-005 — Ops Resilience & Access Verification

> **Summary:** Ensure ClawdBot has verified access to all tools, APIs, and services required for every cron/process — with fallbacks and remote recovery when things break.

**Domain:** clawd/ops
**Priority:** 🔴 CRITICAL
**Status:** CAPTURED
**Type:** EXPLOIT
**Cat:** 🟠 M
**Owner:** 🤖 Rich
**Maturity:** L1
**Next Action:** Map all tools/services used by all crons → build verification script
**Created:** 2026-02-21
**Pipeline:** v1.1
**Field Guide:** task-system/task-field-guide.md

## Dependencies
- **Hard →** None — root infra task
- **Downstream (blocks):** All cron reliability, all automated processes
- **Domain checklist:** clawd/ops

## Win State
Before any cron fires, Rich can verify all required access is live. When access breaks, Rich can either self-heal or escalate with specific diagnosis. Remote recovery possible without Jamie at the machine.

## Steps
| # | Input | Action | Output | Owner |
|---|-------|--------|--------|-------|
| 1 | List of all crons + processes | Map every tool/API/service each one needs | Access matrix: cron × service | 🤖 |
| 2 | Access matrix | Build verification script that checks each service | `scripts/ops-health.js` — returns pass/fail per service | 🤖 |
| 3 | Verification script | Add to daily pre-flight (run before first cron of day) | Pre-flight cron at 05:00 | 🤖 |
| 4 | Failure scenarios | Define fallback for each service failure | Fallback matrix in this file | 🔄 |
| 5 | Fallback matrix | Implement self-heal where possible (token refresh, restart, retry) | Auto-recovery in script | 🤖 |
| 6 | Non-self-healable failures | Build remote recovery playbook | Documented: how to fix from phone/laptop via Claude Code / Codex web | 🔄 |

## Subtasks
| # | Type | Task | Status | Owner | Notes |
|---|------|------|--------|-------|-------|
| 1 | EXPLOIT | Map all cron/process → tool/service dependencies | CAPTURED | 🤖 | |
| 2 | EXPLOIT | Build ops-health verification script | CAPTURED | 🤖 | |
| 3 | EXPLOIT | Pre-flight cron (05:00 daily) | CAPTURED | 🤖 | |
| 4 | EXPLORE | Define fallback for each failure type | CAPTURED | 🔄 | Some need Jamie input |
| 5 | EXPLOIT | Self-heal: token refresh, gateway restart, service restart | CAPTURED | 🤖 | |
| 6 | EXPLOIT | Remote recovery playbook (Claude Code / Codex web / SSH) | CAPTURED | 🔄 | |
| 7 | EXPLOIT | Gateway access: ensure restart/config from remote | CAPTURED | 🤖 | |

## Access Matrix (to be filled by subtask 1)
| Service | Used By | Check Method | Self-Heal? | Fallback |
|---------|---------|-------------|------------|----------|
| Anthropic API | Main session, sub-agents | Auth test | Token refresh | Switch to Gemini |
| Google/Gemini API | Default model, sub-agents | Auth test | — | Switch to Anthropic |
| Expandi API | Health check, sync crons | `expandi-status.js` | — | Browser fallback |
| PhantomBuster API | Profile/activity scraping | API ping | Cookie refresh | Manual |
| H1 Google Sheet | All outreach tasks | Read test | — | Alert Jamie |
| Gmail/IMAP | CR detection | Connection test | Reconnect | Polling fallback |
| Browser (clawd profile) | LinkedIn research, Expandi dashboard | CDP ping | Restart Chrome | Alert Jamie |
| OpenClaw Gateway | All crons, all sessions | Status check | `openclaw gateway restart` | SSH / remote |
| Neo4J | KPI storage, graph queries | Connection test | — | Skip KPI write |
| Master repo (GitHub) | All pushes | `git push --dry-run` | Auth refresh | Alert Jamie |

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|
