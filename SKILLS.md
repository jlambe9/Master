# SKILLS.md — Skills Registry

*A "skill" is a standalone set of instructions an agent can use for a specific task.*
*Every skill has a SKILL.md with frontmatter (name + description) and execution instructions.*
*Full definitions: ClawdBot `STRUCTURE.md`*

## Skill Status Legend
- **ACTIVE** — deployed and verified working
- **TESTING** — deployed but unverified or unreliable
- **BROKEN** — deployed but not functioning
- **PLANNED** — designed but not yet deployed
- **DEPRECATED** — replaced or abandoned

## Registry

### LinkedIn Outreach Skills (Domain: `boss/lead-gen.md`)

| Skill | Location | Status | Process Step | LinkedIn Account | Last Verified |
|-------|----------|--------|-------------|-----------------|---------------|
| linkedin-outreach | ClawdBot: `skills/linkedin-outreach/` | ACTIVE | Pipeline entry point | — | 2026-02-11 |
| write-intro-messages | ClawdBot: `skills/write-intro-messages/` | ACTIVE | P5: Intro writing | Jamie Alexander | 2026-02-11 |
| detect-new-connections | ClawdBot: `skills/detect-new-connections/` | ACTIVE | P4: CR detection | Jamie Alexander (Expandi) | 2026-02-11 |
| pb-activity-extractor | ClawdBot: `skills/pb-activity-extractor/` | TESTING | P12.1B: Activity scraping | Jamie Sandy | 2026-02-11 |
| pb-profile-scraper | ClawdBot: `skills/pb-profile-scraper/` | ACTIVE | P12.1A: Profile scraping | Jamie Sandy | 2026-02-11 |
| sync-expandi-h1 | ClawdBot: `skills/sync-expandi-h1/` | ACTIVE | Expandi↔H1 sync | — | 2026-02-11 |
| expandi | ClawdBot: `skills/expandi/` | TESTING | P3: Connection requests | Jamie Alexander | 2026-02-11 |

### Utility Skills (Domain: `boss/infrastructure.md`)

| Skill | Location | Status | What It Does | Domain | Last Verified |
|-------|----------|--------|-------------|--------|---------------|
| grok-search | ClawdBot: `skills/grok-search/` | ACTIVE | Web + X/Twitter search | infrastructure | 2026-02-11 |
| Ad Wizard | Claude web: bodycog-ad-wizard | ACTIVE | Ad creative production | lead-gen | 2026-02-09 |
| Academic research MCP | Cursor | ACTIVE | PubMed/SciHub queries | research | — |
| Heartbeat protocol | ClawdBot: `HEARTBEAT.md` | TESTING | Proactive check-ins | infrastructure | 2026-02-09 |

### LinkedIn Accounts (Quick Reference)

| Profile | Connections | Assigned To |
|---------|-------------|-------------|
| Jamie Alexander | ~5,500 | Expandi, manual outreach, browser research |
| Jamie Sandy | ~300 | PhantomBuster scraping |
| Jamie Lambe | ~2,000 | Reserve (not assigned) |

⚠️ Full details: ClawdBot `reference/linkedin-account-registry.md`

## Skills Needed (Gap Analysis)

| Skill Needed | Would Support | Priority | Blocked By |
|-------------|---------------|----------|------------|
| Follow-up automation | Lead nurture FU1-breakup | HIGH | No CRM / process defined |
| Intent scoring skill | P12.2: LLM scoring | HIGH | Script exists, needs skill packaging |
| ICP filter skill | P10: Anti-ICP screen | MEDIUM | Script exists, needs skill packaging |
| Sales call booking | Sales workflow | HIGH | No process defined |
| Client onboarding | Product delivery | CRITICAL | No process defined |
| Content scheduling | Organic lead gen | MEDIUM | No content calendar |

## How to Verify a Skill Works

1. **Functional:** Executes without errors
2. **Output quality:** Output is usable without significant rework
3. **KPI impact:** Measurable change in linked metric
4. **Reliability:** Works consistently over 5+ uses

Skill is only ACTIVE if it passes 1-3. Otherwise TESTING.

*Last updated: 2026-02-11*
