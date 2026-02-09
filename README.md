# /master — Coordination Layer

Control plane for all of Jamie's projects, tools, and life domains.

## Quick Start (any AI tool, any session)

1. Read `STATUS.md` — what's active, what stage, what's next
2. Read `task-system/README.md` — how tasks are categorised (E/B/A/M) and routed
3. If working on BodyCog business → read `boss/BOSS.md` for goals/KPIs
4. If working on a specific domain → read the relevant file in `boss/` or `domains/`
5. If planning/sequencing tasks → load `task-system/jamie-profile.md` (Layer 1) and check `task-system/task-log.md` for existing profiles
6. If unsure where something lives → check `RESOURCES.md`
7. If unsure if a process exists → check `PROCESSES.md`
8. If unsure if a skill/tool works → check `SKILLS.md`

## During Session

- Work normally in whatever tool you're in
- Log significant decisions to `DECISIONS.md`
- After completing a task: log execution to `task-system/task-log.md` (~15 sec)
- Use `templates/daily-review.md` format for daily logs → `logs/daily/`

## Ending Session

- Update `STATUS.md` with current state
- If a task changed stage (plan → explore → exploit), update it
- If a decision was made, log it in `DECISIONS.md`
- Run evening plan: review tomorrow's tasks using `templates/evening-plan.md`

## Automated (ClawdBot)

- Full integration guide: `agents/clawdbot.md` (boot order, task routing, sync rules)
- Evening: compile daily log → `logs/daily/`
- Weekly: compile weekly review → `logs/weekly/`
- Continuous: `git pull` / `git push` to keep current

## File Size Rule

Every file stays under 80 lines. If it grows beyond that, split it or push detail to the relevant domain repo and link here.
