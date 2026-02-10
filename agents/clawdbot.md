# ClawdBot ↔ /master Integration Guide

*ClawdBot's AGENTS.md (auto-injected) controls boot. This file is loaded via AGENTS.md step 5 or on-demand. It defines how ClawdBot reads and writes to /master.*

## Ownership Rule

| Owns | Source |
|------|--------|
| Agent identity, tools, skills, behavioral rules, PLAN.md execution queue | ClawdBot workspace (~/clawd) |
| Business state, shared task list, processes, cognitive profile, interventions | /master repo (~/Master) |
| **Conflict?** /master wins for business data. ClawdBot files win for agent behavior. |

## Relationship: PLAN.md vs STATUS.md

- **STATUS.md** = cross-tool truth. All tools see it. Jamie/Cursor updates it.
- **PLAN.md** = ClawdBot's personal execution queue. Derived from STATUS.md but ClawdBot-owned.
- **tasks/BC-xxx.md** = ClawdBot's working notes per task. Not in /master.
- **task-system/** = cognitive routing layer (E/B/A/M classification). Consult when profiling tasks.

## Boot Sequence (AGENTS.md handles steps 1-4, then:)

5. Read this file for /master integration rules
6. Read `task-system/jamie-profile.md` — Jamie's cognitive profile (load once, stable)

## When a Task Appears

```
1. Identify domain → which boss/ or domains/ file?
2. Check PROCESSES.md → is this process defined?
     YES → load the process doc (location in PROCESSES.md table)
     NO  → flag to Jamie: "No process mapped for [task]. Map it now or do ad-hoc?"
           If mapping: use templates/process-map.md → add to PROCESSES.md
3. Check task-system/task-log.md → profiled before?
     YES → auto-fill category, predicted failure point, intervention
     NO  → score with task-system/layer0-scoring.md (~2-3 min one-time)
           → assign E/B/A/M category
           → if B or A: load task-system/intervention-library.md → compose stack
4. Present to Jamie: category | intervention | estimated duration | predicted failure point
```

## After Completing Work

1. **DO NOT edit STATUS.md directly** — you and Cursor/Jamie write to the same repo concurrently. Editing STATUS.md causes merge conflicts.
2. Append to `status/clawdbot-log.md` — what you did, result, any flags for Jamie, and what STATUS.md update is needed (Jamie/Cursor will apply it)
3. Log execution to `task-system/task-log.md` — actual category, actual difficulty, notes
4. If a decision was made → log to `DECISIONS.md`
5. `git add -A && git commit -m "clawdbot: [brief description]" && git push origin main -q`

## Evening Routine (extends ClawdBot's existing 21:30 cron)

ClawdBot already runs evening review → `journal/logs/`. Additionally:
1. Append summary to `status/clawdbot-log.md` (what other tools should know)
2. Optionally prepare tomorrow using `templates/evening-plan.md` → save to `logs/daily/`
3. Commit and push /master

## Weekly Routine (Sunday evening)

1. Compile weekly review using `templates/weekly-review.md` → save to `logs/weekly/YYYY-WNN.md`
2. Check `task-system/experiments.md` for observations due
3. Commit and push /master

## Git Sync Rules

- Pull before reading /master (stale data = wrong decisions)
- Push after any write to /master (other tools need to see changes)
- If merge conflict: keep both versions, flag to Jamie, do not force-push
- Commit messages: `clawdbot: [verb] [what]` (e.g., `clawdbot: update STATUS.md after outreach`)

## Files You Should Never Edit

- `STATUS.md` — Jamie/Cursor only. Log your updates to `status/clawdbot-log.md` instead.
- `task-system/jamie-profile.md` — only Jamie or his explicit instruction
- `boss/BOSS.md` goals/targets — only Jamie
- `RESOURCES.md` tool statuses — only Jamie confirms these
