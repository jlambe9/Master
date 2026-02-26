# BOOT.md — Session Start

## Coordination Layer
**Path:** ~/Master
**Repo:** https://github.com/jlambe9/Master.git

On session start: `cd ~/Master && git pull -q && cat STATUS.md`
On session end: append to `status/clawdbot-log.md` (NOT STATUS.md) → `cd ~/Master && git add -A && git commit -m "clawdbot: [desc]" && git push`

## Quick Reference
- Injected files (always loaded): AGENTS.md, SOUL.md, USER.md, TOOLS.md, HEARTBEAT.md
- On-demand files: MEMORY.md, CHANNELS.md, FEEDBACK.md, NORTHSTAR.md, framework docs
- Shared state: ~/Master/STATUS.md
- Task integration: ~/Master/agents/clawdbot.md
- Expandi runbook: skills/expandi/RUNBOOK.md
