# SKILLS.md — Skills Registry

*A "skill" is a defined capability deployed on a specific tool.
Track: does it exist, does it work, what does it impact, when did we last verify?*

## Skill Status Legend
- **ACTIVE** — deployed and verified working
- **TESTING** — deployed but unverified or unreliable
- **BROKEN** — deployed but not functioning
- **PLANNED** — designed but not yet deployed
- **DEPRECATED** — replaced or abandoned

## Registry

| Skill | Tool | Status | Process It Supports | KPI Impacted | Last Verified | Evidence It Works |
|-------|------|--------|--------------------|--------------|--------------|--------------------|
| Ad Wizard (bodycog-ad-wizard) | Claude web | ACTIVE | Ad creative production | Lead gen: ad volume | 2026-02-09 | Generates compliant creatives; conversion data TBD |
| Expandi monitoring | ClawdBot | TESTING | LinkedIn outreach | Lead gen: outreach/day | [NEEDS VERIFICATION] | Script runs; no volume data yet |
| LinkedIn intro writing | ClawdBot | TESTING | Intro messages | Lead gen: reply rate | [NEEDS VERIFICATION] | Rules defined; no reply data yet |
| Grok search (X/web) | ClawdBot | ACTIVE | Research, monitoring | N/A (support skill) | [NEEDS VERIFICATION] | Returns results |
| Academic research MCP | Cursor | ACTIVE | Thesis research | Research: papers reviewed | [NEEDS VERIFICATION] | PubMed/SciHub queries work |
| Heartbeat protocol | ClawdBot | TESTING | Proactive check-ins | N/A (operational) | [NEEDS VERIFICATION] | Fires but noisy |
| Frontend design | Claude web | ACTIVE | Landing pages, dashboards | Conversion rate | — | Built-in skill, works |

## Skills Needed (Gap Analysis)

| Skill Needed | Would Support | Priority | Blocked By |
|-------------|---------------|----------|------------|
| Follow-up automation | Lead nurture | HIGH | CRM setup |
| Sales call booking | Sales | HIGH | No process defined |
| Content scheduling | Lead gen: content | MEDIUM | No content calendar |
| Daily review automation | Operational rhythm | MEDIUM | ClawdBot restructure |
| Client onboarding flow | Product delivery | CRITICAL | No process defined |
| Outcome tracking dashboard | Product measurement | HIGH | No clients yet |

## How to Verify a Skill Works

1. **Functional test:** Does it execute without errors?
2. **Output quality:** Is the output usable without significant manual rework?
3. **KPI impact:** Can we measure a change in the linked KPI?
4. **Reliability:** Does it work consistently over 5+ uses?

Update this file when: a skill is deployed, tested, breaks, or gets deprecated.
A skill is only ACTIVE if it passes tests 1-3. Otherwise it's TESTING.
