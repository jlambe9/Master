# STATUS.md — What's Active Right Now

*Last updated: 2026-02-11*
*Updated by: ClawdBot*

*Pipeline v1.0: CAPTURED → GOAL CLARITY → DECOMPOSED → SEQUENCED → PLANNED → INITIATED → IN PROGRESS → COMPLETED → PERSISTED | BLOCKED*
*Priority: 🔴 CRITICAL  🟡 HIGH  ⚪ MEDIUM — see `task-system/pipeline.md` for gate checks*
*Cat: 🟢E 🟡B 🔴A 🟠M — see `task-system/interventions.md`*
*Task files: `tasks/[REF].md` — detail, subtasks, execution log*

## 🔴 Active (max 3)

| Task | Ref | Priority | Status | Type | Domain | Next Action |
|------|-----|----------|--------|------|--------|-------------|
| Build Pipeline v2: pre-screen, pre-write, auto-send | BC-065 | 🔴 | DECOMPOSED | EXPLOIT | boss/lead-gen | 7 subtasks — see tasks/BC-065.md |
| Outreach cron audit — all necessary automations | BC-067 | 🔴 | DECOMPOSED | EXPLOIT | boss/lead-gen | List all crons, validate, implement missing |
| Finalize intro message rules for ClawdBot | BC-052 | 🔴 | DECOMPOSED | EXPLOIT | boss/lead-gen | Superseded by BC-065 |
| Find all connections without intros written | BC-062 | 🔴 | COMPLETED | EXPLOIT | boss/lead-gen | Done — 90 accepts mapped |
| Write personalized intros for new connections | BC-063 | 🔴 | IN PROGRESS | EXPLOIT | boss/lead-gen | 33 written, 3 outstanding |
| Fix overnight failure cascade | CLAWD-001 | 🔴 | DECOMPOSED | EXPLOIT | clawd/reliability | Implement 4 fixes (fallback model, cron hours, isolated sessions, compaction) |

## 🟡 Queued

| Task | Ref | Priority | Status | Type | Domain | Blocked By |
|------|-----|----------|--------|------|--------|------------|
| What happens payment → first session | BOSS-ONBOARD | 🔴 | CAPTURED | EXPLORE | boss/product | Before first client |
| Legal docs to operate (GDPR, contracts, T&Cs) | BOSS-GDPR | 🔴 | CAPTURED | EXPLORE | boss/legal-hr | Before first client |
| Build outreach funnel visibility | BC-058 | 🟡 | GOAL CLARITY | EXPLORE | boss/lead-gen | Audit what Expandi tracks |
| Manual 100 daily CRs (backup if Expandi fails) | BC-043 | ⚪ | CAPTURED | EXPLOIT | boss/lead-gen | Backup — use if needed |
| Lead → call → close → onboard process | BOSS-SALES | 🟡 | CAPTURED | EXPLORE | boss/sales | Need leads first |
| Auto-score tasks with cognitive profile | META-TASK-SYSTEM | 🟡 | CAPTURED | EXPLORE | meta | — |
| 14-day free challenge as conversion mechanism | — | 🟡 | CAPTURED | EXPLORE | boss/lead-nurture | Outreach live |
| Short-form video content pipeline | BC-042 | ⚪ | CAPTURED | EXPLORE | boss/lead-gen | Content strategy |
| Set weekly KPI targets + 90/30-day goals | — | ⚪ | CAPTURED | ADMIN | boss | Jamie input |
| Monthly expenses calculation (inc. medication + new flat) | FIN-001 | 🔴 | CAPTURED | EXPLOIT | personal/finance | — |
| Complete financial audit (bills, due dates, payment plans, double rent) | FIN-002 | 🔴 | CAPTURED | EXPLOIT | personal/finance | FIN-001 |
| 3-6 month financial plan (survival maths) | FIN-003 | 🔴 | BLOCKED | EXPLOIT | personal/finance | FIN-001, FIN-002 |
| Business KPIs from financial reality (daily actions über alles) | FIN-004 | 🔴 | BLOCKED | EXPLOIT | boss/finance | FIN-003 |
| Financial timeline plan (what happens when) | FIN-005 | 🔴 | BLOCKED | EXPLOIT | personal/finance | FIN-002, FIN-003 |
| Discuss finances with Saida | FIN-006 | 🟡 | BLOCKED | EXPLOIT | personal/relationship | FIN-002, FIN-003 |
| Write "moving in talk" with Saida (expectations, timelines, tension) | REL-001 | 🟡 | CAPTURED | EXPLORE | personal/relationship | FIN-003 (partial) |
| Proactive relationship plan (actions, gestures, joint projects) | REL-002 | 🟡 | CAPTURED | EXPLOIT | personal/relationship | — |
| Organise regular cleaner | LA-001 | ⚪ | CAPTURED | EXPLORE | personal/life-admin | — |
| Clean flat | LA-002 | ⚪ | CAPTURED | ADMIN | personal/life-admin | — |
| Do washing | LA-003 | ⚪ | CAPTURED | ADMIN | personal/life-admin | — |
| Revise thesis for journal publication | — | ⚪ | CAPTURED | EXPLOIT | research | Time allocation |

## 🟢 Recently Completed

| Task | Date | Notes |
|------|------|-------|
| Rebuild Expandi + ICP screening | 2026-02-10 | BC-057 — campaign live with ICP filters |
| ClawdBot ↔ Master integration | 2026-02-10 | AGENTS.md wired, status/clawdbot-log.md write surface, concurrency-safe |
| ClawdBot file restructure | 2026-02-10 | ~2.7K token boot (from ~15K), on-demand loading |
| Task system integration | 2026-02-09 | E/B/A/M, Layer 0-3, interventions, process mapping |
| Master repo scaffold | 2026-02-09 | 34 files, BOSS system, templates |

## ⚠️ Verification Needed (Jamie — ~2 min)

| Item | File | Question |
|------|------|----------|
| GoHighLevel | RESOURCES.md, finance.md | Active? What plan? Monthly cost? |
| Linear | RESOURCES.md | Still using? Connected to anything? |
| Google AI Pro | RESOURCES.md | Monthly cost? Still needed? |
| Obsidian | RESOURCES.md | Still using? If not, remove |
| 12-month goals | boss/BOSS.md:19 | Still current? Confirm or update |
| Growth roadmap | boss/BOSS.md:77 | Still the plan? Months may have shifted |
| CPD renewal | domains/research/thesis.md | Current? When due? |
| Website/landing page | boss/infrastructure.md | Exists? URL? |

## 📌 Pins
- ClawdBot running on Opus 4.6 [CONFIRMED]
- Cowork fix: remove academic-research MCP server [CONFIRMED]
- Revenue target: £14,750/month [CONFIRMED]
- Morning cardio non-negotiable — mobile tasks only [CONFIRMED]
| Setup Pencil app (whiteboard) | LIFE-001 | ⚪ | CAPTURED | ADMIN | personal/life-admin | — |
| Gmail access for CR acceptance monitoring (auto-sync to H1) | BC-064 | 🔴 | CAPTURED | EXPLOIT | boss/lead-gen | Jamie creates App Password for jlambe9@gmail.com |
| Google Calendar access (proactive scheduling, reminders, event awareness) | CLAWD-002 | 🟡 | CAPTURED | EXPLOIT | clawd/integrations | Jamie grants access or creates service account scope |
| Setup calendar tracking (jamie@bodycog.com) for call booking | BC-066 | 🟡 | CAPTURED | EXPLOIT | boss/lead-gen | Needs Google Calendar API access for bodycog account |
