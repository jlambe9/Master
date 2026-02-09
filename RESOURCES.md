# RESOURCES.md — Where Everything Lives

*If you can't find it here in 30 seconds, this index is broken.*

## Repos

| Repo | Purpose | Location | Key Files |
|------|---------|----------|-----------|
| /master | Coordination layer (this repo) | GitHub + local | STATUS.md, boss/BOSS.md |
| bodycog-marketing | Marketing, outreach, ads, funnels | Cursor workspace | campaigns/, content/, leads/ |
| bodycog-admin | HMRC, finances, company docs | Cursor workspace | expenses/, filings/ |
| thesis | Academic research, lit review, protocols (~1.5B tokens) | Cursor workspace | database/, protocols/, papers/ |
| prior-map | Depth psychology hobby project | Cursor workspace | — |
| ClawdBot workspace | Agent files for Rich | Mac Mini ~/.openclaw/workspace/ | BOOT.md, PLAN.md, SOUL.md |

## Cross-Repo Key Files

| What | Where | Notes |
|------|-------|-------|
| LinkedIn leads (canonical) | H1 Google Sheet, column J | Single source of truth for intros |
| Personal DRI (nutrition) | ClawdBot: nutrition/jamie-personal-dri.json | Genetic-adjusted |
| ClawdBot rewrite spec | Claude web chat + /master DECISIONS.md | Deployed via ClawdBot |
| Ad creative framework | bodycog-marketing/ads/ or Claude web ad-wizard skill | 14DC + 1-2-1 campaigns |
| BPS Signature design | thesis/protocols/ | Design phase |

## Tools

| Tool | Purpose | Status | Critical? | Last Verified |
|------|---------|--------|-----------|---------------|
| Claude web (Max) | Strategy, planning, artifacts | ACTIVE | Yes | 2026-02-09 |
| ClawdBot (Rich) | Autonomous agent, execution | ACTIVE | Yes | 2026-02-09 |
| Cursor + Claude Code | Development, research | ACTIVE | Yes | 2026-02-09 |
| Cowork | Desktop automation | ACTIVE (limited) | No | 2026-02-09 |
| claude-mem | Claude Code session memory | NOT INSTALLED | No | — |
| Linear | Task management | ACTIVE | Yes | [NEEDS VERIFICATION] |
| Google AI Pro | Alternative reasoning | ACTIVE | No | [NEEDS VERIFICATION] |
| Expandi | LinkedIn outreach | TESTING | Yes | [NEEDS VERIFICATION] |
| PhantomBuster | Lead extraction | TESTING | Yes | [NEEDS VERIFICATION] |
| GoHighLevel | CRM | [NEEDS VERIFICATION] | Yes | — |
| Meta Ads Manager | Paid ads | NOT YET ACTIVE | Future | — |
| Obsidian | Knowledge management | [NEEDS VERIFICATION] | No | — |

## Credentials
All passwords: 1Password CLI → `op item get "[service]"`
