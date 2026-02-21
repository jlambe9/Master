# Task Field Guide — How to Fill Out Task Files

*Reference for any agent creating or updating tasks. Linked from every task template.*
*Source of truth for: owner classification, task levels, field definitions, RTP graduation, maturity.*

## Completion Gate

A task is NOT done until every output in its Win State "Outputs" list verifiably exists. Steps and subtasks each have an "Output (proof of completion)" column — these must also exist.

No vague win states. No self-reporting without verification. If the outputs aren't defined, the task can't be completed — it needs output definitions first.

Full protocol: ~/clawd/AGENTS.md → Step 5: Mark Completion.

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

## Dependency Types

### Hard Dependency (→)
Can't physically proceed without this. The input literally doesn't exist yet.
- "Can't send intros without intros being written"
- "Can't calculate survival maths without knowing monthly expenses"
- Notation in task files: **Hard →** [task ID]

### Soft Dependency (~>)
Makes it better / more effective, but you CAN proceed without it.
- "Offer doc makes sales calls better but you can still have conversations"
- "Dashboard is nice but you can read H1 manually"
- Notation in task files: **Soft ~>** [task ID]

### Threshold Dependency (⊕)
Proceeds when a quantitative condition is met. The upstream task doesn't "complete" — it produces signal that accumulates until a threshold triggers the downstream task.
- "Don't build course until ≥10 signups"
- "Don't invest in automation until process run 5+ times manually"
- Notation: **Threshold ⊕** [task ID] ⊕ [condition] [source: where metric lives]

**Three components:**
1. Source task — producing the signal
2. Metric + threshold — what's measured, what triggers
3. Source location — where the scanner reads the current value (H1 column, execution log count, KPI node)

**Scanner behaviour:**
- Below threshold → report: "X at 3/10. 7 to go."
- At ≥80% → flag: "X at 8/10 — start preparing."
- Met → change downstream status: WAITING → CAPTURED. Alert Jamie.

**Neo4J translation:**
```cypher
(downstream:Task)-[:DEPENDS_ON {type: 'threshold', metric: 'signups', threshold: 10, current: 3, source: 'H1:columnX'}]->(upstream:Task)
```

### How to classify
Ask: "If this upstream task didn't exist at all, could I still physically DO the downstream task?"
- NO → Hard dependency
- YES but worse → Soft dependency
- YES but only after enough signal/evidence → Threshold dependency

## Domain Operational Checklists

When Atlas traces a dependency chain to the root of a domain, it must check the domain's operational checklist before declaring "no blockers." These checklists verify that the infrastructure/tools/access for that domain are actually running.

### boss/lead-gen
- [ ] Expandi campaign active + sending CRs
- [ ] Expandi queue loaded with leads
- [ ] Expandi session connected (not expired)
- [ ] PhantomBuster cookies valid
- [ ] H1 sheet accessible + columns correct
- [ ] Intro writing skill functional (browser or PB data)
- [ ] Gmail monitoring active (CR acceptance detection)
- [ ] LinkedIn account not restricted

### boss/sales
- [ ] Offer document exists (BC-OFFER-V1)
- [ ] Call prep template exists (BC-PRECALL-PREP)
- [ ] Call notes template exists (BC-CALL-NOTES)
- [ ] Calendly / booking link active
- [ ] Payment system active (Stripe?)

### boss/product
- [ ] Program structure defined
- [ ] Onboarding process exists (BOSS-ONBOARD)
- [ ] Client app functional (BC-CLIENT-APP) — or manual alternative
- [ ] Assessment tools ready (PSS-10, PANAS)

### boss/legal-hr
- [ ] Privacy policy written
- [ ] Client contract template exists
- [ ] T&Cs written
- [ ] GDPR compliance documented

### personal/finance
- [ ] Bank access available
- [ ] All accounts/bills identified
- [ ] Spreadsheet or tool for tracking

### clawd/ops
- [ ] OpenClaw running + stable
- [ ] Cron jobs active + delivering
- [ ] Browser profile (clawd) functional
- [ ] API keys valid (Anthropic, Google, Expandi, PB)
- [ ] Master repo accessible + pushable

### Atlas Dependency Tracing Rules
When tracing upstream to find root blockers:
1. Follow HARD dependencies only for "what's physically blocking progress"
2. Note SOFT dependencies separately as "would improve effectiveness"
3. When you reach the root of a domain chain (no more upstream tasks), CHECK the domain operational checklist
4. If a checklist item is failing → THAT is the true root blocker, not any task
5. Report: "Root blocker for [domain]: [checklist item] is not operational"

## File Map — Task System Architecture

*This field guide is the central reference. Here's where everything else lives:*

| File | What It Is | When to Read |
|------|-----------|-------------|
| **task-field-guide.md** (this file) | Central reference: how to fill tasks, owner rules, deps, maturity, domain checklists, tracing | Always — this is home base |
| `pipeline.md` | Pipeline stages, gate checks, per-stage failure analysis | When advancing a task through stages |
| `template-v1.2.md` | The actual template to copy when creating a task | When creating a new task |
| `layer0-scoring.md` | 12 computational dimensions for scoring | When scoring a task (agent layer) |
| `jamie-profile.md` | Jamie's CHC/7BES profile for scoring | When scoring a task (agent layer) |
| `interventions.md` | Category routing (E/B/A/M) + pattern recognition | When a task is B/A and needs intervention |
| `intervention-library.md` | Stack composition + conflict table | When composing intervention stacks |
| `intervention-drivers.md` | Per-driver intervention menus | When selecting specific interventions |
| `checklists/README.md` | Architecture for operational checklists (hierarchy) | When building or understanding checklists |
| `checklists/global-infra.md` | Global pre-flight: APIs, gateway, browser, repos | Daily pre-flight (05:00) |
| `checklists/boss-lead-gen-expandi.md` | Full Expandi upstream pipeline checklist | When Expandi stops or lead-gen breaks |
| `~/clawd/reference/personas.md` | Atlas persona + dependency tracing rules | When doing systems/process work |
| `~/Master/TASK-REGISTRY.md` | Canonical list of all task profiles | When creating/finding/scanning tasks |

*If you can't find something, check this file map first. If it's not listed, it might not exist yet — create it.*

## Filing Rules

- Task files: ~/Master/tasks/[ID].md
- Registry: ~/Master/TASK-REGISTRY.md (mirrored to ~/clawd/TASK-REGISTRY.md)
- Process reference: this file (~/Master/task-system/task-field-guide.md)
- Template: ~/Master/task-system/template-v1.1.md
- Scoring: ~/Master/task-system/layer0-scoring.md
- Profile: ~/Master/task-system/jamie-profile.md
