# Task Registry — Canonical Task Library

*Every task type that exists in the system. Profiles, not instances.*
*Mirrored: ~/Master/TASK-REGISTRY.md ↔ ~/clawd/TASK-REGISTRY.md*
*Last scanned: 2026-02-20*

## How This Works

- **Profile** = a task *type*. "Write LinkedIn Intros" is a profile. It persists.
- **Instance** = a single execution of a profile. "Write intros on 2026-02-20" is an instance. It's a row in the execution log.
- **Maturity** = Level 0-9 (see task-system/pipeline.md). Cron/manual scan determines level from file evidence.
- **Owner** = who executes: 🤖 Rich | 🧑 Jamie | 🔄 Hybrid | ❓ Undefined

## Owner Definitions

| Tag | Meaning | Daily Bucket |
|-----|---------|-------------|
| 🤖 Rich | Rich can handle end-to-end given context/output/tools | Bucket 1: Rich autonomous |
| 🔄 Hybrid | Rich does sub-tasks, Jamie reviews/unblocks/decides | Bucket 2: Rich + Jamie handoff |
| 🧑 Jamie | Jamie must execute (ideally recorded for future automation) | Bucket 3: Jamie only |
| ❓ Undefined | Not yet determined — needs exploration | Triage needed |

---

## boss/lead-gen

| ID | Task | Status | Priority | Owner | Maturity | Format Gaps |
|----|------|--------|----------|-------|----------|-------------|
| BC-052 | Define Intro Reference Spec | DECOMPOSED | 🔴 | 🔄 Hybrid | L3 (resourced) | Missing: execution log, outcome table |
| BC-057 | Rebuild Expandi + ICP Screening | COMPLETED | 🔴 | 🔄 Hybrid | L5 (validated) | ✅ Complete |
| BC-058 | Pipeline Tracking Infrastructure | GOAL CLARITY | 🟡 | 🤖 Rich | L1 (scoped) | Missing: steps, subtasks, execution log |
| BC-062 | Find Unwritten Intro Profiles | GOAL CLARITY | 🔴 | 🤖 Rich | L7 (auto-built) | Script exists (`check-intro-backlog.js`). Missing: formal process doc |
| BC-063 | Write Personalized Intros | BLOCKED | 🔴 | 🤖 Rich | L4 (working) | Has execution history. Missing: outcome table, v1.1 fields |
| BC-065 | Pipeline v2 (Pre-Screen, Pre-Write, Auto-Send) | DECOMPOSED | 🔴 | 🤖 Rich | L2 (mapped) | 7 subtasks defined, none started. Missing: execution log |
| BC-067 | Outreach Cron Audit | IN PROGRESS | 🔴 | 🤖 Rich | L3 (resourced) | Has subtasks. Missing: outcome table |
| BC-DAILY-OUTREACH | Morning Outreach Priority Block | CAPTURED | 🔴 | 🔄 Hybrid | L1 (scoped) | Missing: steps, process doc, execution log. Has win state. |
| BC-INTRO-VELOCITY | Max Intro Sending Velocity | IN PROGRESS | 🔴 | 🔄 Hybrid | L2 (mapped) | Missing: execution log, outcome table |

## boss/sales

| ID | Task | Status | Priority | Owner | Maturity | Format Gaps |
|----|------|--------|----------|-------|----------|-------------|
| BOSS-SALES | Sales Call Workflow | CAPTURED | 🟡 | ❓ Undefined | L0 (uncharted) | Missing: everything below win state |
| BC-OFFER-V1 | Define V1 Coaching Offer | CAPTURED | 🔴 | 🔄 Hybrid | L1 (scoped) | Has win state + context. Missing: steps, process |
| BC-PRECALL-PREP | Sales Call Prep Skill (Sandler) | CAPTURED | 🔴 | 🤖 Rich | L1 (scoped) | Has dependencies. Missing: steps, execution log |
| BC-CALL-NOTES | Sales Call Notes Template | CAPTURED | 🔴 | 🔄 Hybrid | L1 (scoped) | Has dependencies. Missing: steps |

## boss/product

| ID | Task | Status | Priority | Owner | Maturity | Format Gaps |
|----|------|--------|----------|-------|----------|-------------|
| BOSS-ONBOARD | Client Onboarding Process | CAPTURED | 🔴 | ❓ Undefined | L0 (uncharted) | Missing: everything below win state |
| BC-CLIENT-APP | Client-Facing ADHD App | CAPTURED | 🟡 | 🤖 Rich | L1 (scoped) | Detailed vision doc. Missing: steps, execution log |

## boss/legal-hr

| ID | Task | Status | Priority | Owner | Maturity | Format Gaps |
|----|------|--------|----------|-------|----------|-------------|
| BOSS-GDPR | GDPR/Legal Compliance | CAPTURED | 🔴 | 🔄 Hybrid | L1 (scoped) | Has win state. Missing: steps, process |

## boss/finance → personal/finance

| ID | Task | Status | Priority | Owner | Maturity | Format Gaps |
|----|------|--------|----------|-------|----------|-------------|
| FIN-001 | Monthly Expenses Calculation | CAPTURED | 🔴 | 🧑 Jamie | L1 (scoped) | Has win state. Missing: steps. Jamie needs to sit down with bank statements. |
| FIN-002 | Complete Financial Audit | CAPTURED | 🔴 | 🧑 Jamie | L1 (scoped) | Blocked by FIN-001. Missing: steps |
| FIN-003 | 3-6 Month Financial Plan | BLOCKED | 🔴 | 🔄 Hybrid | L1 (scoped) | Blocked by FIN-001, FIN-002. Rich can model once Jamie provides data. |
| FIN-004 | Business KPIs from Financial Reality | BLOCKED | 🔴 | 🤖 Rich | L1 (scoped) | Blocked by FIN-003. Rich can compute once FIN-003 done. |
| FIN-005 | Financial Timeline Plan | BLOCKED | 🔴 | 🔄 Hybrid | L1 (scoped) | Blocked by FIN-002, FIN-003. |
| FIN-006 | Discuss Finances with Saida | BLOCKED | 🟡 | 🧑 Jamie | L1 (scoped) | A-I task. Blocked by FIN-002, FIN-003. |

## personal/relationship

| ID | Task | Status | Priority | Owner | Maturity | Format Gaps |
|----|------|--------|----------|-------|----------|-------------|
| REL-001 | "Moving In Talk" with Saida | CAPTURED | 🟡 | 🔄 Hybrid | L1 (scoped) | Rich can draft framework. Jamie has the conversation. |
| REL-002 | Proactive Relationship Plan | CAPTURED | 🟡 | 🔄 Hybrid | L1 (scoped) | Rich can suggest actions. Jamie executes. |

## personal/life-admin

| ID | Task | Status | Priority | Owner | Maturity | Format Gaps |
|----|------|--------|----------|-------|----------|-------------|
| LA-001 | Organise Cleaner | CAPTURED | ⚪ | 🤖 Rich | L1 (scoped) | Rich can research + book. Jamie approves. |
| LA-002 | Clean Flat | CAPTURED | ⚪ | 🧑 Jamie | L0 (uncharted) | Physical task. Minimal spec needed. |
| LA-003 | Do Washing | CAPTURED | ⚪ | 🧑 Jamie | L0 (uncharted) | Physical task. Embedded in daily-rail transitions. |

## clawd/reliability + integrations + ops

| ID | Task | Status | Priority | Owner | Maturity | Format Gaps |
|----|------|--------|----------|-------|----------|-------------|
| CLAWD-001 | Fix Overnight Failure Cascade | DECOMPOSED | 🔴 | 🤖 Rich | L2 (mapped) | 4 subtasks. Missing: execution log |
| CLAWD-003 | Live Business Dashboard | CAPTURED | 🟡 | 🤖 Rich | L1 (scoped) | Vision doc. Missing: steps, process |
| CLAWD-004 | Daily Task Template Scan | CAPTURED | 🟡 | 🤖 Rich | L1 (scoped) | 16:00 daily cron. Scan all tasks for v1.1 gaps + auto-fix |

## meta/task-system

| ID | Task | Status | Priority | Owner | Maturity | Format Gaps |
|----|------|--------|----------|-------|----------|-------------|
| META-TASK-SYSTEM | Task Tracker v1.1 | IN PROGRESS | 🟡 | 🤖 Rich | L4 (working) | Pipeline + template built. Validation pending. |

---

## Registry Stats

| Metric | Count |
|--------|-------|
| Total task profiles | 30 |
| 🤖 Rich (autonomous) | 12 |
| 🔄 Hybrid | 11 |
| 🧑 Jamie only | 5 |
| ❓ Undefined | 2 |
| At L0 (uncharted) | 4 |
| At L1 (scoped) | 18 |
| At L2-3 (mapped/resourced) | 5 |
| At L4+ (working+) | 3 |
| COMPLETED | 1 |
| BLOCKED | 5 |
| Missing v1.1 template fields | 28/30 |

## Key Observations

1. **18 of 30 tasks are stuck at L1 (scoped)** — they have a win state but no steps. The bottleneck is decomposition.
2. **28 of 30 tasks are not in v1.1 format** — no Layer 0 scoring, no outcome tracking, no owner field.
3. **5 tasks are BLOCKED** — all in the FIN chain. FIN-001 is the keystone blocker.
4. **12 tasks are Rich-autonomous** — these can run without Jamie once context is provided.
5. **The finance chain (FIN-001→006) is the most critical blocked sequence** — everything downstream depends on Jamie sitting down with bank statements.
