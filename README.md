# /master — Coordination Layer

Control plane for all of Jamie's projects, tools, and life domains.

## Quick Start (any AI tool, any session)

1. Read `STATUS.md` — what's active, what stage, what's next
2. If working on BodyCog business → read `boss/BOSS.md` for goals/KPIs
3. If working on a specific domain → read the relevant file in `boss/` or `domains/`
4. If unsure where something lives → check `RESOURCES.md`
5. If unsure if a process exists → check `PROCESSES.md`
6. If unsure if a skill/tool works → check `SKILLS.md`

## During Session

- Work normally in whatever tool you're in
- Log significant decisions to `DECISIONS.md`

## Ending Session

- Update `STATUS.md` with current state
- If a task changed stage (plan → explore → exploit), update it
- If a decision was made, log it in `DECISIONS.md`

## Automated (ClawdBot)

- Evening: compile daily log → `logs/daily/`
- Weekly: compile weekly review → `logs/weekly/`
- Continuous: `git pull` / `git push` to keep current

## File Size Rule

Every file stays under 80 lines. If it grows beyond that, split it or push detail to the relevant domain repo and link here.
