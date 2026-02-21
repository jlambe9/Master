# BC-PRECALL-PREP — Sales Call Prep Skill (Sandler Framework)

> **Summary:** Skill that auto-generates a Sandler-structured call plan when a sales call is booked. Pulls all data, identifies gaps, generates targeted questions.

**Domain:** boss/sales
**Priority:** 🔴 CRITICAL
**Status:** CAPTURED
**Type:** EXPLOIT
**Cat:** 🔴 A-S
**Owner:** 🤖 Rich
**Next Action:** Build `skills/pre-call-prep/SKILL.md` with full Sandler process
**Created:** 2026-02-11
**Pipeline:** v1.1

## Win State
When Jamie says "I've got a call with [Name]", Rich immediately produces a Sandler call plan: all known data structured, gaps identified, questions ready. Jamie skims before call and is prepared.

## Trigger
- Jamie tells Rich a call is booked → skill runs immediately
- OR: `callBooked` column in H1 populated → auto-trigger (future)

## Steps
| # | Input | Action | Output |
|---|-------|--------|--------|
| 1 | Lead name + H1 data + PB data + LinkedIn DMs | Pull all available intelligence | Raw data compiled |
| 2 | Raw data + Sandler 7-stage framework | Structure into call plan sections | Sandler-structured call plan |
| 3 | Call plan | Identify information gaps | Gap list + targeted questions |
| 4 | Full call plan | Output to Jamie (Telegram or file) | Ready-to-use call prep doc |

## Call Plan Structure (Sandler 7-Stage)

**Section 1: RAPPORT PREP** — Business, role, shared context, personal hooks, conversation history
**Section 2: UP-FRONT CONTRACT** — Pre-written agenda, time, outcome framing
**Section 3: PAIN EXPLORATION PREP** — Known pain points, pain level assessment, deepening questions (L1→L2→L3)
**Section 4: BUDGET NOTES** — Capacity signals, framing for budget conversation
**Section 5: DECISION PROCESS** — Who decides, timeline signals, priority ranking
**Section 6: FULFILLMENT PREP** — Offer mapped to their specific pain, tailored talking points, objection prep

### Sandler Pain Funnel (3 Levels)
- **L1 Surface:** What's going on? Tell me more. Be specific. Give example.
- **L2 Business Impact:** How long? What tried? Did it work? Cost?
- **L3 Personal Impact:** How affecting you personally? How feel? Given up?

Third-level pain = buying motivation. People buy to fix personal pain.

## Data Sources (priority order)
1. H1 sheet (all columns)
2. RESEARCH tab (bio, posts, problem indicators)
3. PB activity data (post history)
4. LinkedIn DM history
5. Sales Nav export
6. aiNotes column

## Subtasks
| # | Type | Task | Status | Owner |
|---|------|------|--------|-------|
| 1 | EXPLOIT | Build `skills/pre-call-prep/SKILL.md` | CAPTURED | 🤖 Rich |
| 2 | EXPLOIT | Create `reference/call-plan-template.md` | CAPTURED | 🤖 Rich |
| 3 | EXPLOIT | Wire to H1 `callBooked` trigger | CAPTURED | 🤖 Rich |
| 4 | EXPLOIT | Test with mock call | CAPTURED | 🔄 |

## Dependencies / Links
- **Upstream:** BC-OFFER-V1 (offer document referenced in Fulfillment stage), BC-CALL-NOTES (notes template used during call)
- **Downstream:** Sales calls (this prepares Jamie for calls), BOSS-SALES (part of overall workflow)
- **Related:** BC-CLIENT-APP (coach report feeds into prep for coaching calls)

## Decision Log
- 2026-02-11: Created. Jamie specified Sandler (not SPIN). Seven stages: Bonding, Up-Front Contract, Pain (3 levels), Budget, Decision, Fulfillment, Post-Sell.
- 2026-02-11: Corrected SPIN → Sandler. Key difference: qualify budget + decision BEFORE presenting offer.

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🔴 A-S | |
| Failure point | None (Rich autonomous) | |
| Duration | 3h ⚠️ REVIEW | |
| Intervention | None — Rich builds skill | |
| Effectiveness | | |

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | Med | Sandler framework known, data integration novel |
| Procedure specification | Specified | Sandler 7-stage fully documented |
| Procedure complexity | Moderate | Multi-source data pull + structuring |
| Temporal delay | Immediate | Build skill once, use instantly |
| Error cost | Moderate | Bad prep → unprepared call |
| Reward magnitude | High | Every sales call better |
| Reward probability | Guaranteed | Skill produces output |
| Value density per unit | High | Direct sales enablement |
| Feedback latency | Delayed | Validated on real call |
| Process legibility | Clear | Template + sections |
| Model maturity | Familiar | Data aggregation pattern known |
| State-tracking load | Low | Build once |

### 0B: Channel Requirements
- **Input route:** Data reading (Gc,Grw) → Rich handles
- **Processing route:** Semantic structuring (Gc,Gf) → Rich handles
- **Output route:** Formatted document → Rich handles
- **Channel flexible:** N/A — Rich autonomous build
- **Mismatch flags:** None

### 0C: Affective Load
| Dimension | Present | Intensity |
|-----------|---------|-----------|
| Interpersonal risk | N | — (building skill, not doing call) |
| Status challenge | N | — |
| Exposure / visibility | N | — |
| Uncertain return | N | — |
| Confrontation potential | N | — |
| Identity-relevant outcome | Y | Low — sales infrastructure |

### Layer 3 Computation
- **Epistemic value:** Medium (Sandler integration)
- **Pragmatic value:** High
- **Effort cost:** Low (Rich autonomous)
- **Threat:** Low
- **Dominant signal:** → 🔴 A-S (mild identity, fully structurable)

### Predicted Failure Point
- **Stage:** None (Rich autonomous)
- **Cause:** N/A
- **Auto-intervention:** N/A

### Intervention Stack (if B/A)
N/A — 🤖 Rich autonomous build

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-11 | Initial creation with full Sandler framework | Rich |
| 1.1 | 2026-02-21 | Reformatted to v1.1 template, condensed framework | Atlas |
