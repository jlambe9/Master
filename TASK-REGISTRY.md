# Task Registry — Canonical Task Library

*Every task type that exists in the system. Profiles, not instances.*
*Mirrored: ~/Master/TASK-REGISTRY.md ↔ ~/clawd/TASK-REGISTRY.md*
*Last scanned: 2026-02-21 (Atlas v1.1 reformat)*

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

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| BC-052 | Define Intro Reference Spec | DECOMPOSED | 🔴 | 🟡 B | 🔄 Hybrid | L3 (resourced) | ✅ |
| BC-057 | Rebuild Expandi + ICP Screening | COMPLETED | 🔴 | 🟠 M | 🔄 Hybrid | L5 (validated) | ✅ |
| BC-058 | Pipeline Tracking Infrastructure | GOAL CLARITY | 🟡 | 🟢 E | 🤖 Rich | L1 (scoped) | ✅ |
| BC-062 | Find Unwritten Intro Profiles | GOAL CLARITY | 🔴 | 🟡 B | 🤖 Rich | L7 (auto-built) | ✅ |
| BC-063 | Write Personalized Intros | BLOCKED | 🔴 | 🟡 B | 🤖 Rich | L4 (working) | ✅ |
| BC-065 | Pipeline v2 (Pre-Screen, Pre-Write, Auto-Send) | DECOMPOSED | 🔴 | 🟢 E | 🤖 Rich | L2 (mapped) | ✅ |
| BC-067 | Outreach Cron Audit | IN PROGRESS | 🔴 | 🟢 E | 🤖 Rich | L3 (resourced) | ✅ |
| BC-DAILY-OUTREACH | Morning Outreach Priority Block | CAPTURED | 🔴 | 🔴 A-S | 🔄 Hybrid | L1 (scoped) | ✅ |
| BC-INTRO-VELOCITY | Max Intro Sending Velocity | IN PROGRESS | 🔴 | 🔴 A-S | 🔄 Hybrid | L2 (mapped) | ✅ |

## boss/sales

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| BOSS-SALES | Sales Call Workflow | CAPTURED | 🟡 | 🔴 A-S | 🔄 Hybrid | L0 (uncharted) | ✅ |
| BC-OFFER-V1 | Define V1 Coaching Offer | CAPTURED | 🔴 | 🔴 A-S | 🔄 Hybrid | L1 (scoped) | ✅ |
| BC-PRECALL-PREP | Sales Call Prep Skill (Sandler) | CAPTURED | 🔴 | 🔴 A-S | 🤖 Rich | L1 (scoped) | ✅ |
| BC-CALL-NOTES | Sales Call Notes Template | CAPTURED | 🔴 | 🔴 A-S | 🔄 Hybrid | L1 (scoped) | ✅ |

## boss/product

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| BOSS-ONBOARD | Client Onboarding Process | CAPTURED | 🔴 | 🔴 A-S | 🔄 Hybrid | L0 (uncharted) | ✅ |
| BC-CLIENT-APP | Client-Facing ADHD App | CAPTURED | 🟡 | 🔴 A-S | 🤖 Rich | L1 (scoped) | ✅ |

## boss/legal-hr

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| BOSS-GDPR | GDPR/Legal Compliance | CAPTURED | 🔴 | 🔴 A-S | 🔄 Hybrid | L1 (scoped) | ✅ |

## personal/finance

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| FIN-001 | Monthly Expenses Calculation | CAPTURED | 🔴 | 🔴 A-S | 🧑 Jamie | L1 (scoped) | ✅ |
| FIN-002 | Complete Financial Audit | CAPTURED | 🔴 | 🔴 A-S | 🧑 Jamie | L1 (scoped) | ✅ |
| FIN-003 | 3-6 Month Financial Plan | BLOCKED | 🔴 | 🔴 A-I | 🔄 Hybrid | L1 (scoped) | ✅ |
| FIN-004 | Business KPIs from Financial Reality | BLOCKED | 🔴 | 🟢 E | 🤖 Rich | L1 (scoped) | ✅ |
| FIN-005 | Financial Timeline Plan | BLOCKED | 🔴 | 🔴 A-S | 🔄 Hybrid | L1 (scoped) | ✅ |
| FIN-006 | Discuss Finances with Saida | BLOCKED | 🟡 | 🔴 A-I | 🔄 Hybrid | L1 (scoped) | ✅ |

## personal/relationship

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| REL-001 | "Moving In Talk" with Saida | CAPTURED | 🟡 | 🔴 A-I | 🔄 Hybrid | L1 (scoped) | ✅ |
| REL-002 | Proactive Relationship Plan | CAPTURED | 🟡 | 🟢 E | 🔄 Hybrid | L1 (scoped) | ✅ |

## personal/life-admin

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| LA-001 | Organise Cleaner | CAPTURED | ⚪ | 🟡 B | 🤖 Rich | L1 (scoped) | ✅ |
| LA-002 | Clean Flat | CAPTURED | ⚪ | 🟡 B | 🧑 Jamie | L0 (uncharted) | ✅ |
| LA-003 | Do Washing | CAPTURED | ⚪ | 🟡 B | 🧑 Jamie | L0 (uncharted) | ✅ |

## clawd/reliability + integrations + ops

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| CLAWD-001 | Fix Overnight Failure Cascade | DECOMPOSED | 🔴 | 🟠 M | 🤖 Rich | L2 (mapped) | ✅ |
| CLAWD-003 | Live Business Dashboard | CAPTURED | 🟡 | 🟢 E | 🤖 Rich | L1 (scoped) | ✅ |
| CLAWD-004 | Daily Task Template Scan | CAPTURED | 🟡 | 🟢 E | 🤖 Rich | L1 (scoped) | ✅ |

## meta/task-system

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| META-TASK-SYSTEM | Task Tracker v1.1 | IN PROGRESS | 🟡 | 🟢 E | 🤖 Rich | L4 (working) | ✅ |

---

## Registry Stats

| Metric | Count |
|--------|-------|
| Total task profiles | 31 |
| 🤖 Rich (autonomous) | 11 |
| 🔄 Hybrid | 14 |
| 🧑 Jamie only | 5 |
| ❓ Undefined | 0 |
| v1.1 formatted | **31/31** ✅ |
| 🟢 E tasks | 8 |
| 🟡 B tasks | 5 |
| 🔴 A-S tasks | 12 |
| 🔴 A-I tasks | 3 |
| 🟠 M tasks | 2 |
| At L0 (uncharted) | 3 |
| At L1 (scoped) | 19 |
| At L2-3 (mapped/resourced) | 5 |
| At L4+ (working+) | 3 |
| COMPLETED | 1 |
| BLOCKED | 5 |

## Key Observations

1. **All 31 tasks now in v1.1 format** — Layer 0 scored, owner-tagged, process-mapped, intervention stacks assigned.
2. **12 tasks are A-S (structurally aversive)** — Rich can restructure these by doing heavy lifting. Jamie validates.
3. **3 tasks are A-I (intrinsically aversive)** — FIN-003, FIN-006, REL-001. These need intervention stacks, not delegation.
4. **5 tasks are BLOCKED** — all in the FIN chain. FIN-001 is the keystone blocker.
5. **11 tasks are Rich-autonomous** — can run without Jamie once context provided.
6. **The finance chain (FIN-001→006) remains the most critical blocked sequence** — everything downstream depends on Jamie sitting down with bank statements.
7. **0 undefined owners** — every task has a clear owner assignment.
8. **Every task has bidirectional dependencies** — upstream and downstream explicitly mapped.
