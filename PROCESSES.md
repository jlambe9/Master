# PROCESSES.md — Process Registry

*A "process" = a defined business workflow. Documented as a skill (executable) or reference doc.*
*To define a new process: use `templates/process-map.md`. Then add it here and link from the relevant boss/ file.*
*To score a process as a task: use `task-system/layer0-scoring.md` → log to `task-system/task-log.md`.*

## LinkedIn Outreach Pipeline (v0.1)

**Full spec:** ClawdBot: `processes/linkedin-outreach-v0.1.json`
**Summary:** ClawdBot: `processes/linkedin-outreach-v0.1-summary.md`
**Entry skill:** ClawdBot: `skills/linkedin-outreach/SKILL.md`
**Accounts:** ClawdBot: `reference/linkedin-account-registry.md`

| Step | Process | Skill (ClawdBot) | Status | Account |
|------|---------|-------------------|--------|---------|
| 1 | Lead Sourcing | `pb-profile-scraper` | manual | Jamie Sandy |
| 2 | Profile Scraping | `pb-profile-scraper` | ready | Jamie Sandy |
| 3 | Activity Scraping | `pb-activity-extractor` | running | Jamie Sandy |
| 4-7 | ICP Filter + Scoring | LLM scripts (no skill yet) | live | none |
| 8 | Intro Writing | `write-intro-messages` | operational | Jamie Alexander |
| 9 | Connection Requests | `expandi` | live | Jamie Alexander |
| 10 | CR Detection | `detect-new-connections` | operational | Jamie Alexander |
| 11 | Expandi↔H1 Sync | `sync-expandi-h1` | operational | — |
| 12-13 | Send Intros + Follow-ups | Manual (Jamie) | manual | Jamie Alexander |

## ✅ Defined & Active

| Process | Where Documented | Last Verified | Boss Domain |
|---------|-----------------|---------------|-------------|
| LinkedIn outreach pipeline | ClawdBot: `processes/linkedin-outreach-v0.1.json` | 2026-02-11 | lead-gen |
| Intro message writing | ClawdBot: `skills/write-intro-messages/SKILL.md` | 2026-02-11 | lead-gen |
| Connection detection | ClawdBot: `skills/detect-new-connections/SKILL.md` | 2026-02-11 | lead-gen |
| Expandi monitoring | ClawdBot: `skills/expandi/SKILL.md` | 2026-02-11 | lead-gen |
| PB Activity Extraction | ClawdBot: `skills/pb-activity-extractor/SKILL.md` | 2026-02-11 | lead-gen |
| PB Profile Scraping | ClawdBot: `skills/pb-profile-scraper/SKILL.md` | 2026-02-11 | lead-gen |
| Expandi↔H1 Sync | ClawdBot: `skills/sync-expandi-h1/SKILL.md` | 2026-02-11 | lead-gen |
| ClawdBot boot sequence | ClawdBot: `AGENTS.md` | 2026-02-09 | infrastructure |
| ClawdBot heartbeat | ClawdBot: `HEARTBEAT.md` | 2026-02-09 | infrastructure |
| Ad creative production | Claude web: bodycog-ad-wizard skill | 2026-02-09 | lead-gen |

## 🟡 Partially Defined

| Process | What Exists | What's Missing | Boss Domain |
|---------|-------------|----------------|-------------|
| LinkedIn FU sequence | Timing + specs in playbooks/ | Automation, skill file | lead-gen |
| Daily review | Template exists | ClawdBot automation, cron job | infrastructure |
| Thesis research pipeline | MCP tools, Bradford Hill grading | Documented workflow | research |

## ❌ Not Yet Defined

| Process | Priority | Boss Domain | Notes |
|---------|----------|-------------|-------|
| Client onboarding | CRITICAL | product | Must exist before first paying client |
| Sales call workflow | HIGH | sales | Script, booking, follow-up |
| 14-day challenge delivery | HIGH | lead-nurture | Primary conversion mechanism |
| Follow-up sequences | HIGH | lead-nurture | Timing defined, needs automation skill |
| Content publishing (organic) | MEDIUM | lead-gen | Calendar, creation, scheduling |
| GDPR/data handling | HIGH | legal-hr | Before first client |

## File Structure (ClawdBot workspace)

See ClawdBot: `STRUCTURE.md` for full definitions of skills vs references vs pipeline specs.

- **Skills** = Standalone executable instruction sets (`skills/*/SKILL.md`)
- **References** = Supporting docs skills point to (`reference/*.md`)
- **Pipeline specs** = How skills connect as a system (`processes/*.json`)
- **Scripts** = Executable code (`scripts/` or `skills/*/scripts/`)

*Last updated: 2026-02-11*
