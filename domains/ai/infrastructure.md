# AI Infrastructure — Agent Architecture & Cross-Tool Systems

## Current Stack

| Tool | Role | Status | Notes |
|------|------|--------|-------|
| Claude web (Max) | Strategic thinking, artifacts | ACTIVE | Best reasoning, stateless |
| ClawdBot (Rich) | Autonomous agent, execution | ACTIVE | Opus 4.6, restructuring |
| Cursor + Claude Code | Development, research | ACTIVE | MacBook Air |
| Cowork | Desktop automation | ACTIVE | VM disk limited, no heavy MCPs |
| claude-mem | Claude Code session memory | NOT INSTALLED | Ready to install on Mac Mini |
| Linear | Task management | ACTIVE | [NEEDS VERIFICATION] |
| Google AI Pro | Alternative reasoning | ACTIVE | Secondary |

## Architecture Decisions [CONFIRMED]
- Git repo (/master) as coordination layer
- ClawdBot: BOOT.md → PLAN.md → on-demand loading (~1.5k token boot)
- claude-mem for Cursor session persistence (when installed)
- STATUS.md as universal session-start file

## Known Limitations → see PROBLEMS.md

## Security Concerns [PLACEHOLDER — will become major]
- Credential management: 1Password CLI currently
- Agent permissions/boundaries: not formally scoped
- Data privacy across tools: not audited
- MCP server trust model: not evaluated

## Idealised ClawdBot Roadmap (North Star)

### Phase 1 — Revenue Generation (current)
LinkedIn outreach, content, KPI tracking, Expandi monitoring

### Phase 2 — Business Operations (months 2-3)
Market research, revenue forecasting, sales tracking, group coaching mgmt

### Phase 3 — Life Operations (months 3-6)
Email triage, financial management, health tracking, daily/weekly reviews, brain dump processing

### Phase 4 — Life Enhancement (months 6+)
Social calendar, shopping, restaurant booking, travel planning, gamified habits

### Target Agent Architecture
Router (lightweight) → specialist agents: LinkedIn, Content, Research, Task Manager, Health, Finance, Life Admin, Journal
