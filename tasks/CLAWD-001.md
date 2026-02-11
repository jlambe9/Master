# CLAWD-001 — Fix Overnight Failure Cascade (Error Handling & Resilience)

> **Summary:** One Anthropic rate limit at 19:18 on Feb 10 killed all automation for 8+ hours. No backoff, no recovery, no fallback provider. Cron jobs kept retrying into the same wall, resetting cooldown each time. Context overflow errors stacked on top. Need circuit breakers and a non-Anthropic escape hatch.

**Domain:** clawd/reliability
**Priority:** 🔴 CRITICAL
**Status:** DECOMPOSED
**Type:** EXPLOIT
**Cat:** 🟠 M
**Created:** 2026-02-11

## Root Cause Analysis

**Trigger:** Heavy session usage → Anthropic API rate limit hit at 19:18 Feb 10

**Why it cascaded:**
1. **Single-provider dependency** — Primary: Opus. Fallbacks: Sonnet + Opus. All Anthropic. When Anthropic rate-limits, there's zero escape.
2. **Cron jobs on main session** — All 4 crons use `sessionTarget: "main"`, piling onto the same context. Main session was already full → context overflow.
3. **No backoff on cron failures** — Expandi health check fires every 2h. Each attempt hit rate limit, failed, and reset the cooldown window. 8-hour loop.
4. **Stale token errors** — Some retries got 401 auth errors (invalid bearer token) from the cooldown state, adding noise.
5. **Heartbeat amplified it** — `wakeMode: "next-heartbeat"` meant the hourly heartbeat kept triggering failed cron jobs.

**Timeline:**
- 19:18 — First rate limit error
- 19:47 — Cron retry fails (401 + rate_limit)
- 20:17 → 03:00 — Same pattern every hour for 8 hours
- 04:00 — Session recycled, fresh context, API recovered

## Win State
Overnight automation runs reliably. A single rate limit event does NOT cascade into hours of total failure.

## Steps

### 1. Add non-Anthropic fallback model
- Add Google Gemini (key already configured) or XAI Grok as last-resort fallback
- Config: `agents.defaults.model.fallbacks` — append a non-Anthropic model
- Cron jobs can degrade to a cheaper model rather than fail entirely

### 2. Restrict Expandi cron to active hours
- Expandi only sends CRs during 06:00–21:30 London time
- Change cron expr from `0 */2 * * *` to `0 6-21/2 * * *`
- Eliminates pointless overnight retries

### 3. Move cron jobs to isolated sessions
- Change `sessionTarget` from `"main"` to `"isolated"` + `payload.kind` to `"agentTurn"`
- Each cron gets its own clean context — no more piling onto main session
- Main session context stays lean for interactive use

### 4. Evaluate compaction settings
- Current: `mode: "safeguard"` — compaction only fires as last resort
- Consider switching to `mode: "auto"` so long sessions compact before overflowing
- Or set a token threshold for proactive compaction

## KPI / How We Measure
- Zero multi-hour cascading failures
- Cron jobs succeed even when primary provider is rate-limited
- Main session context never overflows due to cron accumulation

## Decision Log
- 2026-02-11 04:56 — Jamie flagged overnight failures. Diagnosed root cause: single-provider + no backoff + main session crons. Created this task.
