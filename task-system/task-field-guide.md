# Task Field Guide — How to Fill Out Task Files

*Reference for any agent creating or updating tasks. Linked from every task template.*
*Source of truth for: owner classification, task levels, field definitions, RTP graduation, maturity.*

## Owner Classification

Owner is NOT permanent. It's a function of how well-defined the task is + whether output can be verified without Jamie. Tasks move 🧑→🔄→🤖 as they mature.

### 🤖 Rich (Bucket 1: Rich E2E)
ALL of these must be true:
- Steps are fully defined (not CAPTURED/GOAL CLARITY)
- Inputs are available (no missing tools/data/access)
- Output is machine-verifiable OR doesn't need human judgment
- No subjective quality gate (e.g. "does this sound right?")

### 🔄 Hybrid (Bucket 2: Rich + Jamie Handoff)
ANY of these:
- Rich can do some steps but Jamie must do others
- Rich produces output but Jamie must review/approve before "done" (e.g. intros — Rich writes, Jamie validates)
- Task has decision points that require Jamie's judgment
- Rich can draft but Jamie makes the final call

### 🧑 Jamie (Bucket 3: Jamie Only)
ANY of these:
- Physical task (clean flat, gym, cooking)
- Requires Jamie's personal presence (Saida conversation, sales call)
- Task is undefined — Jamie's job IS to define it so it can become Hybrid or Rich
- Cannot be done by Rich with verifiable confidence

### ❓ Undefined
- Not enough information to determine owner
- This IS a flag: "Jamie needs to define this further"
- Undefined tasks should be prioritised for definition — they block the pipeline

### Owner Progression
First time doing something → 🧑 Jamie (or ❓)
Process documented, Rich can draft → 🔄 Hybrid
Process proven, output verifiable → 🤖 Rich

## Task Levels

### HEADLINES — Minimal Entry
**When:** Newly captured, early stage, simple one-off (<30 min), insufficient info to spec further.
**Required fields:**
- ID, Name, Summary
- Domain, Priority, Status, Type, Cat
- Owner
- Win State

### FULL SPEC — Complete Task File
**When:** Actively worked or planned, complex, has dependencies.
**Required fields:** All headlines PLUS:
- Steps with Input → Action → Output per step
- Subtasks (if applicable) with owner per subtask
- Dependencies / Links (upstream + downstream)
- Layer 0 scoring (agent layer)
- Intervention stack (if B/A)
- Tools / Inputs needed

### RTP (Repeatable Task Process) — Full Spec + Process Layer
**When:** Task recurs, has been done 2+ times, should be systematised/automated.
**Required fields:** All full spec PLUS:
- Process version (semver: v1.0, v1.1, v2.0)
- Process Version Stack (version history with what changed + why + outcome vs previous)
- Component Registry (all data objects, tools, accounts, files needed)
- Execution Log with 2+ instances
- Automation Requirements (what would need to exist to automate this)
- Maturity level (see below)

## Profiles vs Instances

### Profile
A task *type* in the registry. "Write LinkedIn Intros" is a profile. It persists and evolves.
- Lives as an entry in TASK-REGISTRY.md
- Has a canonical task file in ~/Master/tasks/
- Process steps are versioned (semver) — old versions preserved in Version Stack
- Profile evolves through accumulated instance evidence

### Instance
A single execution of a profile. "Write intros on 2026-02-20" is an instance.
- Lives as a ROW in the profile's Execution Log
- Timestamped: date, duration, outcome, deviations, friction
- Links to the process version it ran under
- NEVER overwrites the profile — it's evidence, not the process
- If an instance reveals the process needs changing → version bump on the profile

### When does a profile version bump?
- **Minor** (v1.0 → v1.1): step reordered, edge case added, resource added
- **Major** (v1.x → v2.0): fundamental restructure, steps replaced, approach changed
- Old versions preserved in Process Version Stack with "why changed" + "outcome vs previous"

## RTP Graduation

A task profile graduates to RTP when ALL RTP-level fields are filled:
- Process steps with Input/Output chains ✅
- Process version (semver) ✅
- Process Version Stack (at least v1.0 entry) ✅
- Component Registry ✅
- Execution Log with 2+ instances ✅
- Automation Requirements documented ✅

Once all fields are filled → maturity = L6 (AUTO-READY).

## Maturity Levels (for RTPs)

| Level | Name | Criteria | What Happens |
|-------|------|----------|-------------|
| L0-L5 | Pre-RTP | Not all RTP fields filled | Task is a profile, not yet an RTP |
| L6 | AUTO-READY | All RTP fields filled, automation requirements documented | Ready to build automation |
| L7 | AUTO-BUILT | Automation exists (script/cron/sub-agent) | Needs testing |
| L8 | AUTO-TESTING | Running with human verification | Track success rate |
| L9 | AUTONOMOUS | 90%+ success rate over 5+ runs, human only for exceptions | Fully autonomous |

### Maturity can drop
If automation breaks or starts failing → drop to L8 or L7. Fix, retest, re-promote.

### How maturity is assessed
The daily template scan (CLAWD-004, 16:00) checks:
1. Which RTP fields are populated → determines if L6
2. Whether automation exists → L7
3. Whether automation has run with verification → L8
4. Success rate across recent instances → L9

## Where to Find Information for Task Fields

| Field | Where to Look |
|-------|--------------|
| Domain | ~/Master/boss/ for business domains, ~/Master/domains/ for personal |
| Priority | Is it blocking revenue (🔴)? On critical path (🟡)? Can wait (⚪)? |
| Category (E/B/A/M) | Score with ~/Master/task-system/layer0-scoring.md + jamie-profile.md |
| Steps | Existing process docs, skill files in ~/clawd/skills/, reference/ files |
| Dependencies | Check TASK-REGISTRY.md for related tasks. Check task files for explicit links. |
| Tools/Inputs | What scripts, APIs, accounts, data does this need? Check ~/clawd/scripts/, skills/ |
| Intervention stack | ~/Master/task-system/intervention-drivers.md + intervention-library.md |
| Component registry | List all data objects that flow through the process steps |
| Automation requirements | What would a script/cron/agent need to do this without Jamie? |
| Win state | Ask: "How does Jamie know this is done?" — must be observable, not "worked on" |

## Filing Rules

- Task files: ~/Master/tasks/[ID].md
- Registry: ~/Master/TASK-REGISTRY.md (mirrored to ~/clawd/TASK-REGISTRY.md)
- Process reference: this file (~/Master/task-system/task-field-guide.md)
- Template: ~/Master/task-system/template-v1.1.md
- Scoring: ~/Master/task-system/layer0-scoring.md
- Profile: ~/Master/task-system/jamie-profile.md
