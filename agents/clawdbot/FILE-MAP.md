# ClawdBot File Map — What I Actually Use

*Snapshot: 2026-02-26*

## 🧠 Core Identity (loaded every session via OpenClaw injection)

| File | Location | Purpose |
|------|----------|---------|
| **SOUL.md** | `~/clawd/SOUL.md` | Who I am. Personality, boundaries, system discipline principles, north star (BPMN→DAG). |
| **AGENTS.md** | `~/clawd/AGENTS.md` | How I operate. Task creation protocol, goal creation protocol, morning briefing format, completion gates, memory rules, strategy/execution boundary. **This is the big one — ~23K chars of operational rules.** |
| **USER.md** | `~/clawd/USER.md` | About Jamie. Currently sparse — most context lives in MEMORY.md. |
| **TOOLS.md** | `~/clawd/TOOLS.md` | Environment-specific notes (cameras, SSH, TTS voices). Currently near-empty. |
| **HEARTBEAT.md** | `~/clawd/HEARTBEAT.md` | Periodic check instructions. Currently empty (heartbeats disabled). |
| **IDENTITY.md** | `~/clawd/IDENTITY.md` | Name, creature type, vibe, emoji. Unfilled template. |

## 🔄 Session Lifecycle

| File | Location | Purpose |
|------|----------|---------|
| **BOOT.md** | `~/clawd/BOOT.md` | Session start instructions: pull Master, read STATUS.md. Session end: commit + push. |
| **MEMORY.md** | `~/clawd/MEMORY.md` | Long-term curated memory. Weltanschauung, unconscious attitude, health goals, outreach data corrections. **Only loaded in 1:1 sessions.** |
| **memory/YYYY-MM-DD.md** | `~/clawd/memory/` | Daily raw logs. Read today + yesterday at session start. |

## 📋 Task System (in ~/Master/task-system/ — the canonical versions)

These are the files AGENTS.md references and enforces:

| File | Purpose |
|------|---------|
| **v1.3-system-overview.md** | Master reference for the entire task system. 13 sections + 4 appendices. Architecture, foundations, data flow, strategy/execution processes, tracing, operational processes, build→run transition, file map, automation, error handling, foundation validation signals (§13 draft). |
| **template-v1.3.md** | Task template. All fields a task can have: headlines through RTP. Includes Layer 0 scoring, intervention stacks, error handling section, decision log, goal linkage. |
| **goal-template-v1.3.md** | Goal template. 8 foundations, mechanism chains, threshold gates, stop criteria. |
| **task-field-guide.md** | Field-by-field reference for filling task templates. Owner classification criteria, dependency types, maturity levels. |
| **strategy-change-protocol.md** | Rules for when/how strategy changes are allowed (weekly review only, not during execution). |
| **intervention-drivers.md** | Maps affective load (0C scores) to intervention stacks for B/A category tasks. |
| **interventions.md** | EBAM category definitions and intervention library. |
| **pipeline.md** | Task pipeline stages (CAPTURED → COMPLETED) with gate checks per stage. |
| **jamie-profile.md** | Jamie's cognitive profile for task scoring. ADHD traits, channel preferences, energy patterns. |
| **layer0-scoring.md** | How to score Layer 0A/0B/0C dimensions. |
| **v1.3-enforcement-rules.md** | What's enforced vs advisory in v1.3. |
| **v1.3-cron-registry.md** | All cron jobs: schedule, purpose, output location. |
| **v1.3-kpi-metrics-design.md** | KPI metrics layer design (not yet implemented). |

## 📊 Shared State (in ~/Master/)

| File | Purpose |
|------|---------|
| **STATUS.md** | What's active right now. Task board. **Stale since 2026-02-11.** |
| **TASK-REGISTRY.md** | All tasks with current status. Mirrored to ~/clawd/. |

## 🤖 Cron Outputs (in ~/clawd/memory/cron-outputs/)

| Directory | Schedule | Purpose |
|-----------|----------|---------|
| **morning-briefing/** | Daily 07:00 | v1.3 format briefing with priorities, traffic lights, buckets |
| **midday-check/** | Daily 13:00 | Progress check against morning 🔴s |
| **evening-block/** | Daily 21:00 | Daily wrap, completion review, domain metrics, tomorrow prep |
| **expandi-health/** | Every 2h (08-22) | Campaign status, CR counts, alerts |
| **sync-expandi-h1/** | Daily 12:00 + 21:00 | Sync Expandi data to H1 Google Sheet |
| **system-health/** | 3x daily (06,12,18) | Cron health, disk space, gateway status |
| **master-validation/** | Daily 22:30 | Validates all other cron outputs exist and are sane |

## 🔧 Key Scripts (in ~/clawd/scripts/)

| Script | Purpose |
|--------|---------|
| **expandi-status.js** | Query Expandi API for campaign metrics |
| **sync-expandi-h1.js** | Sync Expandi campaign data → H1 Google Sheet |
| **gmail-accept-sync.js** | Check Gmail for LinkedIn accept emails → update H1 crAccepted |
| **gmail-accept-sync-state.json** | State file for above (last checked UID) |

## 🎯 Skills (in ~/clawd/skills/)

| Skill | Purpose |
|-------|---------|
| **expandi/** | Expandi API interaction + RUNBOOK.md for troubleshooting |
| **linkedin-outreach/** | Entry point for outreach pipeline — routes to sub-skills |
| **write-intro-messages/** | Write personalised LinkedIn intro messages |
| **mobile-intro-review/** | Send intros to Telegram for Jamie's mobile review |
| **competitor-screen/** | Screen leads for competitors vs customers |
| **detect-new-connections/** | Detect newly accepted CRs via Expandi scraping |
| **sync-expandi-h1/** | Sync Expandi ↔ H1 sheet |
| **pb-profile-scraper/** | PhantomBuster LinkedIn profile scraper |
| **pb-activity-extractor/** | PhantomBuster LinkedIn activity extractor |
| **grok-search/** | Web + X search via Grok |
| **expandi-campaign-setup/** | Create new Expandi campaigns |

## 📁 What's NOT actively used (legacy/archive)

Most of `~/clawd/boss/`, `~/clawd/reference/`, `~/clawd/playbooks/`, `~/clawd/processes/`, `~/clawd/task-system/` are **older versions** that have been superseded by `~/Master/` equivalents. They exist but I don't actively reference them. The canonical versions live in Master.

Same for `~/clawd/tasks/` — these are older task files. Active tasks are in `~/Master/tasks/`.

## 🔑 Credentials (not included in this snapshot)

| File | Purpose |
|------|---------|
| `~/clawd/credentials/google-sheets-service-account.json` | Google Sheets API access |
| `~/clawd/credentials/expandi-config.json` | Expandi API key + campaign IDs |
| `~/clawd/.env` | Gmail credentials (GMAIL_USER, GMAIL_APP_PASSWORD) |
