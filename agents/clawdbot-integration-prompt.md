# Prompt for Claude Web (ClawdBot rewrite chat)

*Copy everything below the line and paste into the Claude web chat where ClawdBot's file structure rewrite was designed.*

---

## Context

We've built a `/master` coordination repo that acts as a control plane across all of Jamie's tools (ClawdBot, Cursor, Claude Code mobile, Claude web). It's a git repo on GitHub.

ClawdBot needs to be aware of /master so it can:
- Read business context and active tasks on boot
- Route tasks using the E/B/A/M cognitive profiling system
- Update shared state after doing work
- Run evening/weekly automated reviews

**We've already written the integration guide from /master's side.** The file `master/agents/clawdbot.md` (which will exist in ClawdBot's workspace after git clone) contains the complete protocol: boot sequence, task encounter flow, after-work updates, evening/weekly routines, git sync rules, and ownership boundaries.

The ownership split is:
- **ClawdBot's own files** → HOW the agent behaves (identity, tools, skills, rules)
- **master/ repo** → WHAT to work on (business state, task queue, processes, cognitive profile)

## What I need from you

**First:** Output ClawdBot's current file structure as you designed it (file names + one-line descriptions). This confirms you still have context. If you can't do this accurately, STOP — the rest of this prompt won't work without that context.

**Then:** Tell me the MINIMAL changes needed to ClawdBot's existing files so that:

1. On boot, after loading BOOT.md, ClawdBot checks for `master/` directory and reads `master/agents/clawdbot.md` for integration instructions
2. ClawdBot knows the master/ repo exists and what it's for (1-2 sentences max in BOOT.md or wherever it fits your architecture)
3. ClawdBot's existing task/planning behavior doesn't conflict with /master's task routing system

## Constraints (CRITICAL — read before responding)

- **ADDITIVE ONLY** — Do not rename, restructure, or delete any existing files
- **MINIMAL** — If you can achieve this with 3 lines added to BOOT.md, do that. Don't restructure
- **EXACT OUTPUT** — Give me the precise text to add and WHERE to add it (e.g., "Add after line X of BOOT.md")
- **NO NEW FILES in ClawdBot's workspace** — The integration logic lives in master/agents/clawdbot.md, not in ClawdBot's own files
- **IF CONFLICT:** If ClawdBot's current files already handle task routing or planning in a way that might conflict with /master's task-system/, flag this explicitly and suggest how to resolve WITHOUT rewriting either system

## What master/agents/clawdbot.md contains (summary)

So you know what ClawdBot will find when it reads this file:

- **Ownership rule:** ClawdBot files = agent behavior, /master = business data. If conflict, /master wins for business data.
- **Boot addition:** After BOOT.md loads → git pull master → read STATUS.md (active tasks, pins) → read jamie-profile.md (cognitive profile, stable)
- **Task encounter:** Check PROCESSES.md for defined process → check task-log.md for prior profile → if missing, score with layer0-scoring.md → assign E/B/A/M category → if B/A, compose intervention from intervention-library.md
- **After work:** Update STATUS.md, log to task-log.md, commit/push
- **Evening:** Compile daily log, prepare tomorrow's plan
- **Weekly:** Compile review, check experiments
- **Git rules:** Pull before read, push after write, never force-push, flag conflicts to Jamie
- **Never edit:** jamie-profile.md, BOSS.md targets, RESOURCES.md tool statuses (Jamie-only)

## Expected output format

```
FILE: [filename]
LOCATION: [after line X / at end of section Y / new section after Z]
ADD:
[exact text to add]
```

If multiple files need changes, repeat the format. If zero files need changes (ClawdBot's architecture already supports this), say so and explain why.
