# AI Infrastructure — Agent Architecture & Cross-Tool Systems

*MCP = Model Context Protocol (tool integration standard). Opus 4.6 = Claude flagship model. For Jamie's cognitive profile (CHC/7BES) and how it affects task routing, see `task-system/jamie-profile.md`.*

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

## Connecting Tools to /master

### ClawdBot (Mac Mini — one-time setup)
```bash
cd ~/.openclaw/workspace && git clone <master-repo-url> master
```
Add to ClawdBot BOOT.md:
```
## Master Context
On boot: read master/STATUS.md
On new task: check master/PROCESSES.md → master/task-system/README.md (diagnosis protocol)
After execution: update master/STATUS.md, commit, push
```
Cron sync (every 15 min):
```bash
*/15 * * * * cd ~/.openclaw/workspace/master && git pull origin main -q
*/15 * * * * cd ~/.openclaw/workspace/master && git add -A && git diff --cached -q || git commit -m "clawdbot: sync $(date +\%F-\%H\%M)" && git push origin main -q
```

### Cursor Workspaces
Add /master as multi-root workspace folder, or symlink:
```bash
ln -s /path/to/master ~/cursor-projects/master
```
Claude Code in any project can then read `/master/STATUS.md` for shared context.

### Claude Code Mobile
Open /master repo directly. Read STATUS.md for current state. Update task logs via commit.
