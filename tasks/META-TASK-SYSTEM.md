# META-TASK-SYSTEM — Expand Task Tracker to v1.1

> **Summary:** Upgrade the task tracking system to automatically score tasks using Jamie's cognitive profile (12 dimensions, channel matching, emotional load) instead of manual classification.

**Domain:** meta/task-system
**Priority:** 🟡 HIGH
**Status:** CAPTURED
**Type:** EXPLORE
**Cat:** 🟢 E
**Created:** 2026-02-10

## Win State
Task pipeline expanded from v1.0 (8 stages + simple gate checks) to v1.1 with full Layer 0 scoring integration, per-stage failure analysis, and intervention auto-selection.

## What v1.1 adds over v1.0
- Full Layer 0 computational scoring (12 dimensions) integrated into gate checks
- Channel requirement analysis (CHC mapping) at DECOMPOSED stage
- Affective load scoring at GOAL CLARITY stage (early A-task detection)
- Per-stage failure point analysis with intervention auto-selection
- Layer 3 prediction formula applied at PLANNED stage
- Expanded pipeline from 8 to potentially 9-10 stages (if research supports it)

## Source Documents (already in /master)
- `task-system/layer0-scoring.md` — 12 computational dimensions (0A), channel requirements (0B), affective load (0C), Layer 3 formula
- `task-system/interventions.md` — pipeline failure points table (lines 33-44), pattern recognition triggers
- `task-system/intervention-library.md` — stack composition, conflict table
- `task-system/intervention-drivers.md` — 6 aversion driver menus
- `task-system/jamie-profile.md` — CHC capacities, 7BES thresholds, pharma context

## KPI / How We Measure
- Time-to-execution for new tasks <5 min (from seeing sequence to starting)
- Prediction accuracy: predicted vs actual E/B/A/M category match rate

## Subtasks
| # | Type | Task | Status | Notes |
|---|------|------|--------|-------|
| 1 | EXPLORE | Review Layer 0 scoring for gate check integration points | CAPTURED | |
| 2 | EXPLORE | Define expanded stage requirements with computational thresholds | CAPTURED | |
| 3 | EXPLOIT | Update pipeline.md with v1.1 definitions | CAPTURED | |
| 4 | EXPLOIT | Update templates/task.md with new fields | CAPTURED | |

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Notes
- v1.0 is deliberately simple: 8 stages, text-based gate checks, 3 priority levels, 3 task types
- v1.1 should integrate the computational scoring WITHOUT making daily use harder
- Key constraint: Jamie doesn't fill in scoring — agents do it automatically
