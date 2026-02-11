# Lead Generation

## Current State
- Primary channel: LinkedIn outreach (Expandi CRs + PhantomBuster scraping + LLM intros)
- Pipeline: v0.1 operational — 37 intros written, 70 CRs/day via Expandi
- Secondary: Organic content (not yet active)
- Paid ads: Not yet active (ad wizard skill exists in Claude web)

## KPIs
| Metric | Target | Actual (Feb 2026) | Source |
|--------|--------|-------------------|--------|
| CRs sent/day | 70 | ~70 | Expandi |
| Accept rate | 41% | 41% | Expandi |
| Intros written | all accepted | 37/60 done | H1 sheet |
| Intros sent/day | 25 | manual (Jamie) | LinkedIn |
| Reply rate | 10% | TBD | Manual |
| Calls booked/week | 11 | 0 | TBD |

## LinkedIn Accounts
| Account | Use | Status |
|---------|-----|--------|
| Jamie Alexander (~5,500) | Expandi CRs, manual outreach | ⚠️ Restricted until 11 Feb 10:57 GMT |
| Jamie Sandy (~300) | PB scraping | Active (PB running) |
| Jamie Lambe (~2,000) | Reserve | Clean |

Full details: ClawdBot `reference/linkedin-account-registry.md`

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
- Funnel maths: `playbooks/linkedin-funnel.md`
- Daily ops: `playbooks/linkedin-daily-ops.md`
- Personalisation: `playbooks/linkedin-personalisation.md`
- Diagnostics: `playbooks/linkedin-diagnostics.md`

## What's Working
- Expandi CRs at 70/day with 41% accept rate
- LLM intro writing producing quality personalised messages
- PB scraping pipeline operational

## What's Not Working
- LinkedIn bot detection triggered (dual-account simultaneous automation)
- Intro sending still manual (Jamie bottleneck)
- No reply data yet — need to start sending intros to measure
