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
| `task-log.md` | Accumulated task profiles + execution history | When a task appears (lookup) |
| `experiments.md` | Active hypotheses, variables, observations | Daily review, weekly patterns |

## Lookup/Create Loop

1. Task appears → identify domain (from boss/ or domains/)
2. Check `task-log.md` — has this task type been profiled?
3. **YES:** Load profile, auto-fill prediction, present to Jamie
4. **NO:** Agent pre-fills Layer 0, Jamie confirms/corrects (~2-3 min one-time)
5. After execution: Jamie notes outcome (~15 sec)
6. System compares prediction to reality, updates profile

## Session Start Format (Layer 2 — Jamie provides, 15 seconds)

| Field | Input | Options |
|-------|-------|---------|
| Energy | Tap one | 🔋High / ⚡Medium / 🪫Low |
| Time | Auto-detected | Morning / Afternoon / Evening |
| State | Optional, 1-3 words | e.g., "slept badly," "post-gym" |

## Key Metric

**Time-to-execution.** If Jamie starts within 5 min of seeing the recommended
sequence, the system is working — regardless of prediction accuracy.
Secondary: automation/delegation conversion rate on flagged B-tasks.
