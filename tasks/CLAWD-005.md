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

## Failure Classification Schema

When something breaks, classify FIRST before tracing:

### Level 1: Gateway / Platform Failure
**Symptoms:** No crons firing, no sessions responding, gateway unreachable
**Tags:** `failure:gateway`, `failure:platform`
**Trace:** Is OpenClaw running? → Is gateway process alive? → Is port 18789 responding? → Is auth token valid?
**Self-heal:** `openclaw gateway restart` → if fails, SSH/remote restart
**Priority:** CRITICAL — nothing works until this is fixed

### Level 2: Service / API Failure  
**Symptoms:** Cron fires but fails on API call, auth error, timeout
**Tags:** `failure:service`, `failure:auth`, `failure:timeout`
**Trace:** Which service? → Is key valid? → Is service up? → Rate limited?
**Self-heal:** Token refresh → fallback model → skip and retry next cycle
**Priority:** HIGH — specific crons/tasks affected, others may still work

### Level 3: Cron / Task Failure
**Symptoms:** Cron runs, service works, but output is wrong/incomplete/missing context
**Tags:** `failure:cron-logic`, `failure:context`, `failure:tool-access`
**Trace:** Did the agent have the right prompt? → Right tools? → Right files? → Was context too large / compacted?
**Self-heal:** Re-run with fixed prompt → provide missing context → adjust tool access
**Priority:** MEDIUM — system is healthy, specific task needs fixing

### Level 4: Data / State Failure
**Symptoms:** Everything runs but data is stale, wrong, or inconsistent
**Tags:** `failure:data-stale`, `failure:data-inconsistent`, `failure:sync`
**Trace:** When was last successful sync? → Which source is authoritative? → Is there a sync conflict?
**Self-heal:** Force re-sync → rebuild from authoritative source
**Priority:** MEDIUM — may produce wrong outputs silently

### Pre-flight Trace Order
Always diagnose top-down: Level 1 → 2 → 3 → 4. Don't debug cron logic if the gateway is down.

### Neo4J Schema Properties (for error tracking)
```cypher
(:Error {
  id: 'ERR-YYYY-MM-DD-NNN',
  level: 1-4,
  tags: ['failure:gateway'],
  detected: datetime(),
  service: 'anthropic|expandi|h1|...',
  cronJob: 'job-id',
  selfHealAttempted: true|false,
  selfHealResult: 'success|failed|partial',
  resolved: datetime(),
  resolvedBy: 'self-heal|jamie|rich',
  rootCause: 'description'
})
-[:AFFECTED]->(Task|CronJob)
-[:FIXED_BY]->(Decision)
```

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|
