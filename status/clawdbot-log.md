# ClawdBot Log

## 2026-02-10 15:30

### BC-052 Updates
- Created MVP intro-writing-spec at `~/clawd/reference/intro-writing-spec.md` (v1.0)
- Consolidated template, personalization rules, real good/bad examples, validation criteria into single file
- Updated `~/clawd/processes/write-intro-messages.md` — now references MVP spec, correct column (J), includes daily process

### Intro Writing — Daily Repeat Task
- **Type:** Daily repeat, runs via cron at 21:30 ("Daily Intro Catch-up")
- **Process:** `~/clawd/processes/write-intro-messages.md`
- **Find leads:** `node scripts/check-intro-backlog.js --json` → returns accepted connections with no draft
- **Write intros:** Using `reference/intro-writing-spec.md` (v3 template + layered personalization)
- **Output:** H1 column J only
- **Skip rule:** If insufficient profile data, write SKIP not a generic intro

### STATUS.md suggested updates
- BC-052: Stage → EXPLOIT, next action = "Jamie review MVP spec, then daily execution"
- Add "Write intros for new connections" as daily repeat task in Active

## 2026-02-10 15:30 — BC-064 Created

### New task: BC-064 — Fix Connection Detection → Intro Pipeline
- **Priority:** 🔴 CRITICAL
- **Problem:** Expandi shows 70 connected, H1 has 28 marked. 27 leads need intros. Pipeline has gaps between detection → marking → writing.
- **Task file:** ~/clawd/tasks/BC-064.md
- **Suggested STATUS.md update:** Add BC-064 to Active (replace a completed task), domain boss/lead-gen, stage PLAN

## 2026-02-10 15:45 — BC-064/BC-065 Pipeline Diagnosis Complete

### Root cause
- Expandi uses LinkedIn internal member IDs (ACoAAB...) in URLs
- H1 uses public profile URLs (linkedin.com/in/username)
- Old scripts tried URL matching → only 3 of 50 matched
- Name matching works: 50/50 verified

### Actions taken
- BC-064 updated: v1.0 process = Expandi as source, name matching, mark crAccepted
- BC-065 created: v1.1 = Gmail monitoring (real-time, catches organic, public URLs)
- Process doc created: `~/clawd/processes/detect-new-connections.md`
- Deprecated: mark-connected-leads.js, get-connected-leads.js
- **40 leads need intros, 37 not yet marked crAccepted**

### STATUS.md suggestions
- Add BC-064 (v1.0 pipeline) as Active, stage EXPLOIT
- Add BC-065 (v1.1 Gmail) as Queued

## 2026-02-10 16:05 — BC-064 Subtask 2 Complete + Lifecycle Model

### Execution
- Marked 33 leads as crAccepted in H1 column K (date: 2026-02-10)
- 15 already marked from earlier campaign  
- Intro backlog now at 59 (was 27)
- 9 remaining from Expandi page 2 — will catch tomorrow

### New: Task Lifecycle Model
Created `~/clawd/reference/task-lifecycle.md`
- OPEN → IN PROGRESS → VALIDATE → OPERATIONAL → (DEPRECATED)
- OPERATIONAL = the post-DONE state for repeatable tasks
- OPERATIONAL tasks move from PLAN.md active list to "Running Processes" section
- Rich executes via cron, only alerts Jamie if broken
- Key insight: repeatable tasks are never "done" — they become OPERATIONAL or DEPRECATED

### STATUS.md suggestions
- BC-064: stage VALIDATE
- New section: "Running Processes" for OPERATIONAL tasks

## 2026-02-10 17:55 — Task Template + Process Map Implemented

### New task template
- `~/clawd/reference/task-template.md` — includes process map with input/output chain per step
- Each step tagged: AUTOMATABLE | HUMAN_REVIEW | HUMAN_REQUIRED
- Lifecycle states: OPEN → IN PROGRESS → VALIDATE → OPERATIONAL → DEPRECATED

### BC-064 retrofitted
- Full process map with 3 steps, input→output chains explicit
- Steps 1-2 AUTOMATABLE, Step 3 HUMAN_REVIEW
- All resources, columns, constraints, error handling documented

### BC-066 created (QUEUED)
- Process automation assessment — triggers when 3-5 tasks reach OPERATIONAL
- Will review whether HUMAN_REVIEW steps can be eliminated
- Parked until we have evidence
