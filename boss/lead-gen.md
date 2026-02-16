# Lead Generation

## Current State
- Primary channel: LinkedIn outreach (Expandi CRs + PhantomBuster scraping + LLM intros)
- Pipeline: v0.1 operational — 37 intros written, 70 CRs/day via Expandi
- Secondary: Organic content (not yet active)
- Paid ads: Not yet active (ad wizard skill exists in Claude web)

## KPIs (rebased 2026-02-12 at 35 CRs/day)
| Metric | Target | Actual (Feb 2026) | Source |
|--------|--------|-------------------|--------|
| CRs sent/day | 35 | 35 (paused — weekly LinkedIn cap) | Expandi |
| Accept rate | 42.9% | 42.9% (115/268) | Expandi |
| Intros sent/day | 15 (all accepts) | 18 total sent ever | H1 sheet |
| Intro reply rate | 16.7% | 16.7% (3/18) | H1 sheet |
| Conversations/week | 30 | ~3 | H1 sheet |
| Calls booked/week | 8 | 0 | TBD |
| Calls showed/week | 5-6 | 0 | TBD |
| Closed/week | 1.5 | 0 | TBD |
| Revenue/month | £3,000 (min) | £0 | Pre-revenue |

*Full funnel maths: `playbooks/linkedin-funnel.md` (rebased to 35/day with actuals)*

## LinkedIn Accounts
| Account | Use | Status |
|---------|-----|--------|
| Jamie Alexander (~5,500) | Expandi CRs, manual outreach | ⚠️ Restricted until 11 Feb 10:57 GMT |
| Jamie Sandy (~300) | PB scraping | Active (PB running) |
| Jamie Lambe (~2,000) | Reserve | Clean |

Full details: ClawdBot `reference/linkedin-account-registry.md`

## H1 Sheet: campaignId Column (col AP)
**Format:** `NNN_DDMM` — campaign number + launch date (e.g. `003_1602`)
**Purpose:** Tracks which Expandi campaign batch each lead was allocated to. Set at batch selection, before CRs sent.
**Full column schema:** ClawdBot `processes/linkedin-outreach-process-map.md`

## Skills (ClawdBot)
| Skill | Status | What |
|-------|--------|------|
| `linkedin-outreach` | ACTIVE | Pipeline entry point |
| `write-intro-messages` | ACTIVE | LLM intro writing |
| `detect-new-connections` | ACTIVE | CR detection from Expandi |
| `pb-activity-extractor` | TESTING | PB activity scraping |
| `pb-profile-scraper` | ACTIVE | PB profile scraping |
| `sync-expandi-h1` | ACTIVE | Expandi↔H1 sync |
| `expandi` | TESTING | Expandi monitoring |
| Ad Wizard | ACTIVE | Ad creative (Claude web) |

## Processes
| Process | Documented At |
|---------|--------------|
| Full pipeline (13 steps) | ClawdBot: `processes/linkedin-outreach-v0.1-summary.md` |
| Pipeline spec | ClawdBot: `processes/linkedin-outreach-v0.1.json` |
| FU sequence (FU1–breakup) | `playbooks/linkedin-personalisation.md` |
| Daily ops | `playbooks/linkedin-daily-ops.md` |
| Content creation | NOT YET BUILT |

## Playbooks
- **Full outbound playbook:** `playbooks/linkedin-outbound-playbook.md` (master reference — personalisation, diagnostics, multipliers, levers)
- Funnel maths (35/day, firm): `playbooks/linkedin-funnel.md`
- Daily ops: `playbooks/linkedin-daily-ops.md`
- Personalisation: `playbooks/linkedin-personalisation.md`
- Diagnostics: `playbooks/linkedin-diagnostics.md`

## What's Working
- Expandi CRs at 35/day with 42.9% accept rate (excellent)
- LLM intro writing producing quality personalised messages (16.7% reply rate)
- PB scraping pipeline operational (118 profiles, 5,914 activity records)
- Competitor screening operational (34 flagged from 751)
- Automated health checks, morning briefing, daily intro catch-up (crons)

## What's Not Working
- LinkedIn weekly CR cap limits to ~270/week
- Intro sending still manual (Jamie bottleneck — 92 drafted, unreviewed)
- FU sequence not operational (18 overdue, no templates built)
- No call booking system (no Calendly, no CTA)
- No sales call framework
- No content engine (passive warming not happening)
