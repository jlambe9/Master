# BC-CLIENT-APP — Client-Facing ADHD Coaching App (Clawdbot-Based)

> **Summary:** Productise Clawdbot as the coaching delivery mechanism. Each client gets a private Telegram AI companion that delivers protocol, captures tasks, tracks adherence, and sends consented summaries to Jamie.

**Domain:** boss/product
**Priority:** 🟡 HIGH
**Status:** CAPTURED
**Type:** EXPLORE → EXPLOIT
**Cat:** 🔴 A-S
**Owner:** 🤖 Rich
**Next Action:** Create client workspace template files (subtask 1) — needed for Founders Program
**Created:** 2026-02-11
**Pipeline:** v1.2

## Win State
Working V1 client bot: Telegram-based AI companion for coaching clients. Delivers protocol, captures tasks, tracks adherence, sends consented summaries to Jamie. Tested with first Founders Program client.
**Outputs (completion gate — ALL must exist to mark done):**
1. Working V1 client bot deployed on Telegram
2. Bot delivers protocol, captures tasks, tracks adherence
3. Consented summaries sent to Jamie
4. Tested with first Founders Program client

## Subtasks
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 1 | EXPLOIT | Create client workspace template files | CAPTURED | P1 | 🤖 | ~/clients/[name]/ structure |
| 2 | EXPLOIT | Write client-setup.sh script | CAPTURED | P1 | 🤖 | One-click provisioning |
| 3 | EXPLOIT | Create client-facing SOUL.md persona | CAPTURED | P1 | 🔄 | Not Rich — purpose-built |
| 4 | EXPLOIT | Build coach report cron + format | CAPTURED | P1 | 🤖 | Consented summaries |
| 5 | EXPLOIT | Create onboarding flow (Telegram) | CAPTURED | P1 | 🤖 | 5 questions at Start |
| 6 | EXPLORE | Process recording prototype | CAPTURED | P2 | 🤖 | After first clients |
| 7 | EXPLORE | Friction tagging system | CAPTURED | P2 | 🤖 | Identify highest-leverage automation |
| 8 | EXPLORE | Multi-tenant architecture | CAPTURED | P3 | 🤖 | When >5 clients |
| 9 | EXPLORE | Standalone app feasibility | CAPTURED | P4 | 🤖 | When >20 clients |

## Dependencies / Links
- **Upstream:** BC-OFFER-V1 (defines what Founders Program includes — this is a deliverable), BOSS-ONBOARD (onboarding feeds into client setup)
- **Downstream:** BC-PRECALL-PREP (coach report feeds into call prep)
- **Requires:** Actual coaching clients (Founders Program)

## Product Vision

### Why This Exists
ADHD coaching without a delivery system is broken by design. You're telling people with executive function deficits to remember to do things — that's the problem they're paying you to solve. The app IS the coaching.

### Competitive Moat
No ADHD coach has this. Typical experience: weekly call → forgot what happened → generic advice → repeat. BodyCog: daily AI companion → real-time capture → structured summaries → targeted coaching calls.

### Architecture Evolution
- **V1 (Founders, 3-5 clients):** Separate Clawdbot instance per client on Mac Mini
- **V2 (10+ clients):** Single server, workspace routing, management dashboard
- **V3 (50+ clients):** Purpose-built mobile app, cloud backend

### Privacy & Consent
Client owns data. Jamie sees ONLY consented categories: protocol adherence, task completion, energy/mood, themes, blockers, self-ratings. Raw conversations and journals stay private. Client previews summary before send.

### Daily Workflow
- **Morning (wake+30):** Protocol check, today's focus, energy check-in, calendar preview
- **Midday:** Progress tap, afternoon setup
- **Afternoon:** Available but doesn't initiate unless deadline/reminder
- **Evening (21:00):** Day review (1-10), protocol checklist, tomorrow prep, wind-down

## Key Decisions Needed
1. Client-facing persona — how should the bot sound?
2. Protocol format — how is metabolic protocol structured?
3. Pricing for ongoing bot access post-coaching?
4. Data retention — how long do we keep client data?

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🔴 A-S | |
| Failure point | Decomposition (complex product) | |
| Duration | 2-3 weeks for V1 | |
| Intervention | Rich builds, Jamie validates persona | |
| Effectiveness | | |

## Decision Log
- 2026-02-11: Product vision captured. Key insight: the app IS the coaching delivery mechanism. Telegram = MVP app.
- 2026-02-11: Privacy architecture defined. Client owns data, consented summaries only.
- 2026-02-11: One-click setup concept — script creates workspace, configures gateway, sets up crons.

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | High | Novel product, many design decisions |
| Procedure specification | Partial | Vision clear, implementation open |
| Procedure complexity | Complex | Multi-component system |
| Temporal delay | Weeks | Build → deploy → validate |
| Error cost | Moderate | Bad UX = client churn |
| Reward magnitude | High | Product differentiator |
| Reward probability | Likely | Tech is proven (Clawdbot), application is novel |
| Value density per unit | Med | Exploration phases = variable density |
| Feedback latency | Delayed | Client feedback takes weeks |
| Process legibility | Partial | Complex build, but subtasks are clear |
| Model maturity | Novel | First time building client-facing bot |
| State-tracking load | High | Multiple components to track |

### 0B: Channel Requirements
- **Input route:** Reading + semantic (Gc,Gf) — product design
- **Processing route:** Pattern detection + simultaneous (Gf,Gwm) — architecture
- **Output route:** Writing/code (Gc,Grw) — implementation
- **Channel flexible:** Y — Rich builds
- **Mismatch flags:** None for Rich. Jamie involvement = persona validation (Gc strength)

### 0C: Affective Load
| Dimension | Present | Intensity |
|-----------|---------|-----------|
| Interpersonal risk | N | — |
| Status challenge | N | — |
| Exposure / visibility | Y | Med — product = public-facing |
| Uncertain return | Y | Med — will clients use it? |
| Confrontation potential | N | — |
| Identity-relevant outcome | Y | High — "my product" |

### Layer 3 Computation
- **Epistemic value:** High (novel product design)
- **Pragmatic value:** High (product differentiator)
- **Effort cost:** Med (Rich builds)
- **Threat:** Med (identity + exposure)
- **Dominant signal:** → 🔴 A-S (structurally solvable — Rich builds, Jamie validates)

### Predicted Failure Point
- **Stage:** Decomposition
- **Cause:** Scope creep — vision is ambitious, V1 must be minimal
- **Auto-intervention:** Constrain to P1 subtasks only. V2/V3 are separate.

### Intervention Stack (if B/A)
- **Drivers:** Identity relevance (High), exposure (Med)
- **Stack:** Draft-first ship-later, minimum viable version ("V1 for 3-5 clients"), graduated visibility (private beta first)
- **Confidence:** UNTESTED
- **Conflicts checked:** N

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-11 | Created with full vision | Rich + Jamie |
| 1.1 | 2026-02-21 | Reformatted to v1.1 (condensed vision, preserved all content) | Atlas |
