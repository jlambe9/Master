# ClawdBot ↔ /master Integration Guide

*This file tells ClawdBot how to use the /master coordination repo. ClawdBot's own files (BOOT.md, PLAN.md, SOUL.md) define HOW ClawdBot works. This file defines HOW ClawdBot reads and writes to /master for shared context.*

## Ownership Rule

| Owns | Source |
|------|--------|
| Agent identity, tools, skills, behavioral rules | ClawdBot workspace files |
| Business state, task queue, processes, cognitive profile, interventions | /master repo |
| **Conflict?** Always prefer /master for business data. Always prefer ClawdBot files for agent behavior. |

## Boot Sequence (after ClawdBot's own BOOT.md loads)

1. `git pull origin main -q` in /master directory
2. Read `STATUS.md` — active tasks, queued tasks, pins
3. Read `task-system/jamie-profile.md` — Jamie's cognitive profile (load once, stable)
4. You now have context. Proceed with PLAN.md or await instructions.

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

1. Update `STATUS.md` — move task, change stage, add to completed if done
2. Log execution to `task-system/task-log.md` — actual category, actual difficulty, notes
3. If a decision was made → log to `DECISIONS.md`
4. `git add -A && git commit -m "clawdbot: [brief description]" && git push origin main -q`

## Evening Routine (automated, ~19:00)

1. Compile daily log using `templates/daily-review.md` → save to `logs/daily/YYYY-MM-DD.md`
2. Prepare tomorrow using `templates/evening-plan.md` (context packet for morning cold start)
3. Commit and push

## Weekly Routine (automated, Sunday evening)

1. Compile weekly review using `templates/weekly-review.md` → save to `logs/weekly/YYYY-WNN.md`
2. Check `task-system/experiments.md` for observations due
3. Commit and push

## Git Sync Rules

- Pull before reading /master (stale data = wrong decisions)
- Push after any write to /master (other tools need to see changes)
- If merge conflict: keep both versions, flag to Jamie, do not force-push
- Commit messages: `clawdbot: [verb] [what]` (e.g., `clawdbot: update STATUS.md after outreach`)

## Files You Should Never Edit

- `task-system/jamie-profile.md` — only Jamie or his explicit instruction
- `boss/BOSS.md` goals/targets — only Jamie
- `RESOURCES.md` tool statuses — only Jamie confirms these
