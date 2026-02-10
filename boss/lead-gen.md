# Lead Generation

## Current State [CONFIRMED]
- Primary channel: LinkedIn outreach (Expandi + PhantomBuster)
- Secondary: Organic content (not yet active)
- Paid ads: Not yet active (ad wizard skill exists in Claude web)
- Status: Infrastructure being built, zero outreach volume currently

## KPIs (targets from funnel model — see `playbooks/linkedin-funnel.md`)
| Metric | Target (mid) | Actual | Source |
|--------|-------------|--------|--------|
| CRs sent/day | 50 | 0 | Expandi dashboard |
| Accept rate | 50% | N/A | Expandi dashboard |
| Intros sent/day | 25 | 0 | ClawdBot log |
| Intro reply rate | 10% | N/A | ClawdBot log |
| Conversations/week | 44 | 0 | Manual |
| Calls booked/week | 11 | 0 | Calendly/CRM |
| Calls showed/week | 8 | 0 | Calendly/CRM |
| Closed/month | 8–12 | 0 | CRM |
| Content posts/week | 3 | 0 | Manual |

## Tools [with status]
| Tool | Purpose | Status | Critical? |
|------|---------|--------|-----------|
| Expandi | LinkedIn outreach automation | TESTING | Yes — primary channel |
| PhantomBuster | Lead extraction + enrichment | TESTING | Yes — feeds Expandi |
| LinkedIn (jamie.lam9) | Main profile, 5500 connections | ACTIVE | Yes |
| LinkedIn (jamie@bodycog) | Backup, ~300 connections | ACTIVE | No — backup |
| Meta Ads Manager | Paid campaigns | NOT YET ACTIVE | Future |
| Ad Wizard skill | Ad creative generation | ACTIVE (Claude web) | No — enhancement |

## Processes
| Process | Status | Where Documented |
|---------|--------|-----------------|
| LinkedIn lead extraction | Partial | ClawdBot: skills/expandi/RUNBOOK.md |
| Intro message writing | Partial | ClawdBot: reference/intro-writing-spec.md |
| Follow-up sequence (FU1–FU3 + breakup) | Defined | `playbooks/linkedin-personalisation.md` |
| Daily operations schedule | Defined | `playbooks/linkedin-daily-ops.md` |
| Content creation (organic) | [NOT YET BUILT] | — |
| Ad creative production | Active | Claude web: bodycog-ad-wizard skill |
| Traffic source tracking | [NOT YET BUILT] | — |

## Playbook Reference
- Funnel maths + KPI benchmarks: `playbooks/linkedin-funnel.md`
- Daily ops schedule: `playbooks/linkedin-daily-ops.md`
- Message personalisation specs: `playbooks/linkedin-personalisation.md`
- Diagnostic cheat sheet (low metrics → fixes): `playbooks/linkedin-diagnostics.md`
- Improvement actions + global levers: `playbooks/linkedin-improvement.md`

## Operational Detail
- **Repo:** bodycog-marketing (campaigns/, content/, leads/)
- **Canonical lead list:** H1 Google Sheet (column J = intro messages)

## What's Working
- [NO DATA YET — need first outreach batch]

## What's Not Working
- [NO DATA YET]
