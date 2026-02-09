# Task Routing System

*Cross-cutting task classification and intervention system for all domains.*
*Full specification: https://claude.ai/chat/da4bc234-ed5e-4635-86e4-d60d6f9ebd00*

## Architecture

```
LAYER 0: Task Structure (agent-computed from description)
    ↓
LAYER 1: Jamie's Profile (stable — see jamie-profile.md)
    ↓
LAYER 2: Current State (Jamie inputs at session start — 15 sec)
    ↓
LAYER 3: Predicted Experience (agent computes from 0 × 1 × 2)
    ↓
EXECUTION → LEARNING (prediction vs reality → model updates)
```

## Categories

| Code | Label | Meaning | Intervention |
|------|-------|---------|--------------|
| 🟢 E | Epistemic | High-novelty, engaging | Execute. Time-box if B/A tasks due. |
| 🟡 B | Boring | Low-novelty, draining | Eliminate → Automate → Delegate → Restructure → Time-box |
| 🔴 A-S | Aversive-Structural | Emotional but fixable via restructuring | Restructure, then re-categorise |
| 🔴 A-I | Aversive-Intrinsic | Emotional load won't change with structure | Core to goals? → Growth + support. Not core? → Delegate. |
| 🟠 M | Misrouted | Going through weak cognitive channel | Reroute through strong channel, then re-categorise |

## File Map

| File | What | When to Load |
|------|------|--------------|
| `jamie-profile.md` | Layer 1: CHC, 7BES, precision weights, pharma | At boot |
| `layer0-scoring.md` | Layer 0: dimension definitions for scoring | When profiling a new task |
| `interventions.md` | Category routing, pattern recognition triggers | When selecting intervention |
| `intervention-library.md` | Stack composition, conflict table, validation protocol | When B/A task needs specific support |
| `intervention-drivers.md` | Menus per aversion driver (6 drivers) | When composing intervention stack |
| `task-log.md` | Accumulated task profiles + execution history | When a task appears (lookup) |
| `experiments.md` | Active hypotheses, variables, observations | Daily review, weekly patterns |

## Diagnosis Protocol (when task is undefined)

```
TASK APPEARS → Agent asks: "Is this task defined?"
      │
  Check PROCESSES.md — does a process exist?
  Check task-log.md — does a profile exist?
      │
  BOTH EXIST → Load profile, auto-fill, present to Jamie
      │
  PROCESS MISSING → Map it using templates/process-map.md
    → Identify: trigger, inputs, steps, tools, outputs, win state, edge cases
    → Add to PROCESSES.md registry
    → Link from relevant boss/ domain file
      │
  PROFILE MISSING → Score with layer0-scoring.md, create profile in task-log.md
    → Load jamie-profile.md for mismatch computation
    → Assign category (E/B/A/M), predict failure point
    → If B/A: load intervention-library.md → compose stack
      │
  PRESENT TO JAMIE → with category, intervention, estimated duration
```

## Lookup/Create Loop
1. Task appears → identify domain (from boss/ or domains/)
2. Check `task-log.md` — profiled? **YES:** auto-fill. **NO:** Layer 0 scoring (~2-3 min one-time)
3. After execution: Jamie notes outcome (~15 sec). System compares prediction to reality.

## Session Start (Layer 2 — Jamie, 15 seconds)
Energy: 🔋High / ⚡Medium / 🪫Low · Time: auto-detected · State: optional 1-3 words

## Key Metrics
**Primary:** Time-to-execution (<5 min from seeing sequence = working). **Secondary:** Automation/delegation conversion rate on flagged B-tasks.
