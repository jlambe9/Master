# Task Registry — Canonical Task Library

*Every task type that exists in the system. Profiles, not instances.*
*Mirrored: ~/Master/TASK-REGISTRY.md ↔ ~/clawd/TASK-REGISTRY.md*
*Last scanned: 2026-02-21*
*All tasks reformatted to v1.1+ template with Layer 0 scoring, owner tags, process mapping.*
*LinkedIn pipeline reconciled: 6 LP tasks (v1.2) unify v0.2 processes + 17 lead stages.*

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

### LinkedIn Pipeline (LP series — unified pipeline tasks)
*Wiring doc: ~/Master/task-system/linkedin-pipeline-wiring.md*
*Source specs: processes/linkedin-outreach-v0.2.json + task-system/lead-pipeline-stages.md*

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.2 |
|----|------|--------|----------|-----|-------|----------|------|
| LP-001 | Lead Sourcing & Import | IN PROGRESS | 🔴 | 🟢 E | 🔄 Hybrid | L4 (working) | ✅ |
| LP-002 | Lead Screening & Scoring | IN PROGRESS | 🔴 | 🟢 E | 🤖 Rich | L5 (validated) | ✅ |
| LP-003 | Intro Writing & Review | IN PROGRESS | 🔴 | 🟢 E | 🔄 Hybrid | L5 (validated) | ✅ |
| LP-004 | CR & Intro Delivery | IN PROGRESS | 🔴 | 🟢 E | 🔄 Hybrid | L4 (working) | ✅ |
| LP-005 | Conversation & Close | CAPTURED | 🔴 | 🔴 A-S | 🔄 Hybrid | L2 (mapped) | ✅ |
| LP-006 | Pipeline Infrastructure | IN PROGRESS | 🟡 | 🟢 E | 🤖 Rich | L7 (auto-built) | ✅ |

### Legacy / Component Tasks (subsumed by LP series but still tracked)

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| BC-052 | Define Intro Reference Spec | DECOMPOSED | 🔴 | 🟢 E | 🔄 Hybrid | L3 (resourced) | ✅ |
| BC-057 | Rebuild Expandi + ICP Screening | COMPLETED | 🔴 | 🟠 M | 🔄 Hybrid | L5 (validated) | ✅ |
| BC-058 | Pipeline Tracking Infrastructure | SUBSUMED→LP-006 | 🟡 | 🟢 E | 🤖 Rich | L1 (scoped) | ✅ |
| BC-062 | Find Unwritten Intro Profiles | SUBSUMED→LP-003 | 🔴 | 🟡 B | 🤖 Rich | L7 (auto-built) | ✅ |
| BC-063 | Write Personalized Intros | SUBSUMED→LP-003 | 🔴 | 🟡 B | 🤖 Rich | L4 (working) | ✅ |
| BC-065 | Pipeline v2 (Pre-Screen, Pre-Write, Auto-Send) | SUBSUMED→LP-001-006 | 🔴 | 🟢 E | 🤖 Rich | L2 (mapped) | ✅ |
| BC-067 | Outreach Cron Audit | SUBSUMED→LP-006 | 🔴 | 🟢 E | 🤖 Rich | L3 (resourced) | ✅ |
| BC-DAILY-OUTREACH | Morning Outreach Priority Block | CAPTURED | 🔴 | 🔴 A-S | 🔄 Hybrid | L1 (scoped) | ✅ |
| BC-INTRO-VELOCITY | Max Intro Sending Velocity | SUBSUMED→LP-004 | 🔴 | 🔴 A-S | 🔄 Hybrid | L2 (mapped) | ✅ |

## boss/sales

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| BOSS-SALES | Sales Call Workflow | CAPTURED | 🟡 | 🔴 A-S | ❓ Undefined | L0 (uncharted) | ✅ |
| BC-OFFER-V1 | Define V1 Coaching Offer | CAPTURED | 🔴 | 🔴 A-S | 🔄 Hybrid | L1 (scoped) | ✅ |
| BC-PRECALL-PREP | Sales Call Prep Skill (Sandler) | CAPTURED | 🔴 | 🔴 A-S | 🤖 Rich | L1 (scoped) | ✅ |
| BC-CALL-NOTES | Sales Call Notes Template | CAPTURED | 🔴 | 🔴 A-S | 🔄 Hybrid | L1 (scoped) | ✅ |

## boss/product

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| BOSS-ONBOARD | Client Onboarding Process | CAPTURED | 🔴 | 🔴 A-S | ❓ Undefined | L0 (uncharted) | ✅ |
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
| FIN-006 | Discuss Finances with Saida | BLOCKED | 🟡 | 🔴 A-I | 🧑 Jamie | L1 (scoped) | ✅ |

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
| CLAWD-005 | Ops Resilience & Access Verification | CAPTURED | 🔴 | 🟠 M | 🤖 Rich | L1 (scoped) | ✅ |

## meta/task-system

| ID | Task | Status | Priority | Cat | Owner | Maturity | v1.1 |
|----|------|--------|----------|-----|-------|----------|------|
| META-TASK-SYSTEM | Task Tracker v1.1 | IN PROGRESS | 🟡 | 🟢 E | 🤖 Rich | L4 (working) | ✅ |

---

## Registry Stats

| Metric | Count |
|--------|-------|
| Total task profiles | 37 (31 legacy + 6 LP pipeline) |
| 🤖 Rich (autonomous) | 14 |
| 🔄 Hybrid | 13 |
| 🧑 Jamie only | 5 |
| ❓ Undefined | 2 |
| 🟢 E tasks | 15 |
| 🟡 B tasks | 4 |
| 🔴 A-S tasks | 12 |
| 🔴 A-I tasks | 3 |
| 🟠 M tasks | 2 |
| COMPLETED | 1 |
| SUBSUMED | 6 |
| BLOCKED | 5 |
| IN PROGRESS | 7 |
| v1.2 formatted (LP) | **6/6** ✅ |
| v1.1 formatted (legacy) | **31/31** ✅ |

## Key Observations

1. **All 31 tasks now in v1.1 format** — Layer 0 scored, owner-tagged, process-mapped, dependencies bidirectional.
2. **12 tasks are A-S (structurally aversive)** — most can be restructured via Rich drafting + Jamie reviewing.
3. **3 tasks are A-I (intrinsically aversive)** — FIN-003, FIN-006, REL-001. Need intervention stacks.
4. **5 tasks are BLOCKED** — all in the FIN chain. FIN-001 is the keystone blocker (🧑 Jamie only).
5. **12 tasks are Rich-autonomous** — can run without Jamie once context provided.
6. **The finance chain (FIN-001→006) remains the most critical blocked sequence.** FIN-001 = Jamie sits with bank statements.
7. **Most A-S tasks have a common pattern:** Rich drafts, Jamie reviews. This converts "create from scratch" (A) into "edit existing" (E/B).

## Dependency Map (Critical Path)

```
FIN-001 (Jamie) → FIN-002 (Jamie) → FIN-003 (Hybrid) → FIN-004 (Rich) → BC-DAILY-OUTREACH
                                    → FIN-005 (Hybrid)
                                    → FIN-006 (Jamie) → REL-001

BC-052 (Hybrid) → BC-063 (Rich) → BC-INTRO-VELOCITY
               → BC-065 (Rich) → BC-067 subtasks .12-.17

BC-OFFER-V1 → BOSS-SALES → BOSS-ONBOARD
            → BC-PRECALL-PREP
            → BC-CALL-NOTES
            → BC-CLIENT-APP
```
