# LinkedIn Pipeline Wiring Document

*Single-page map: Stage → Task → Process → Script → Cron → H1 → Validation Gates*
*Created: 2026-02-21 by Atlas*
*Source truth for how the LinkedIn outreach pipeline is wired end-to-end.*

## Architecture

Two complementary views unified here:
- **Lead Stages** (lead-pipeline-stages.md): WHERE the lead is (17 states)
- **Operational Processes** (linkedin-outreach-v0.2.json): WHAT we do (P1-P16)
- **Pipeline v2 Spec** (pipeline-v2-spec.md): WHERE we're going (pre-screen → pre-write → auto-send)

## Reconciliation Notes

| Aspect | v0.2 Processes | 17 Stages | Who Wins |
|--------|---------------|-----------|----------|
| Operational detail (scripts, crons, actors) | ✅ Rich | ❌ Missing | v0.2 |
| Lead state tracking (H1 columns) | ❌ Partial | ✅ Complete gap analysis | Stages |
| Post-sale (Close, Onboard) | ❌ Stub only | ✅ Defined | Stages |
| Infrastructure processes (sync, health, metrics) | ✅ P15/P16/P8 | ❌ Not stages | v0.2 |
| Pipeline v2 ordering (screen before CR) | ❌ v0.2 = screen after source | ✅ v2 spec reorders | v2 Spec |
| Feedback loop | ✅ P9 detailed | ❌ Not a stage | v0.2 |

**Gaps in v0.2:** Post-sale stages (14-17), H1 column gap analysis, v2 ordering
**Gaps in stages:** No operational detail (scripts/crons/actors), no infrastructure processes, no feedback loop

## Unified Pipeline Map

```
LP-001: SOURCED
  ↓ (hard)
LP-002: PROFILE_SCRAPED → PRE_SCREENED → ACTIVITY_SCRAPED → FULL_SCREENED
  ↓ (hard)
LP-003: INTRO_WRITTEN → INTRO_REVIEWED_AI → INTRO_REVIEWED_JAMIE → SEND_MESSAGE
  ↓ (hard)
LP-004: UPLOADED_TO_EXPANDI → CR_SENT → CR_ACCEPTED → INTRO_SENT
  ↓ (hard)
LP-005: IN_CONVERSATION → CALL_BOOKED → CALL_COMPLETED → CLOSED → ONBOARDED
  ↓ (parallel, always-on)
LP-006: Pipeline Infrastructure (sync, health, metrics, feedback)
```

## Stage → Task → Process → Implementation Wiring

| # | Stage | Task | Process | Script(s) | Cron | H1 Columns | Owner |
|---|-------|------|---------|-----------|------|------------|-------|
| 1 | SOURCED | LP-001 | P1 | scripts/add-lead.js | — | fullName, linkedinUrl, sourceDate, sourceBatch, source(AI) | 🔄 |
| 2 | PROFILE_SCRAPED | LP-002.1 | P12.1A | PB Profile Scraper (phantom 3528510028266977) | — | pbProfileScrape | 🤖 |
| 3 | PRE_SCREENED | LP-002.2 | P10, P11, P12.1D(profile) | agent-2-anti-icp.js, agent-3-fit-scorer.js, competitor-screen | — | preScreenResult, preScreenDate, ICP?(F) | 🤖 |
| 4 | ACTIVITY_SCRAPED | LP-002.3 | P12.1B | PB Activity Extractor (phantom 7454781617069280) | — | pbActivityScrape | 🤖 |
| 5 | FULL_SCREENED | LP-002.4 | P12.1D(activity), P12.1C, P12.2 | merge-phantombuster-outputs.js, agent-4-llm-analyzer.js, push-competitor-labels.js | — | screenResult, screenDate, screenNotes, competitor_context(AK) | 🤖 |
| 6 | INTRO_WRITTEN | LP-003.1 | P5.1-P5.4 | generate-intro-ai.js, push-intros-to-sheet.js | 0 2 * * * (overnight) | draft_message(J), aiNotes(AJ), introWrittenDate | 🤖 |
| 7 | INTRO_REVIEWED_AI | LP-003.2 | P5 (validation) | generate-intro-ai.js | — | aiPassed | 🤖 |
| 8 | INTRO_REVIEWED_JAMIE | LP-003.3 | P13 | mobile-intro-review skill | — | jamieReviewed, edits(O), comments(P) | 🔄 |
| 8b | SEND_MESSAGE | LP-003.4 | P5/P13 | — | — | sendMessage | 🔄 |
| 9 | UPLOADED_TO_EXPANDI | LP-004.1 | P3.1 (v2: CSV upload) | (v2: expandi-csv-generator.js — TODO) | — | expandiUploaded, expandiBatch, expandiCampaign | 🤖 |
| 10 | CR_SENT | LP-004.2 | P3.2 | Expandi auto | — | crSent(L) | 🤖 |
| 11 | CR_ACCEPTED | LP-004.3 | P4, P14, P15 | gmail-cr-pipeline.js, sync-expandi-h1.js, check-intro-backlog.js | */10, 3x/day, continuous | crAccepted(K) | 🤖 |
| 12 | INTRO_SENT | LP-004.4 | P5.6-P5.7 (v2: Expandi auto) | — (manual) | — | introSent(Q), introSentMethod | 🧑 (v1) / 🤖 (v2) |
| 13 | IN_CONVERSATION | LP-005.1 | P6, P7 | get-followups-due.js, check-replies.js | — | replied(T), positive(U), conv status(V), firstReplyDate | 🔄 |
| 14 | CALL_BOOKED | LP-005.2 | P7.4 | — | — | callBooked(Y) | 🧑 |
| 15 | CALL_COMPLETED | LP-005.3 | P7.6 | — | — | attended(Z), callResult, callNotesLink | 🧑 |
| 16 | CLOSED | LP-005.4 | BOSS-SALES | — | — | offer(AA), closed won(AB), closed lost(AC), dealValue | 🧑 |
| 17 | ONBOARDED | LP-005.5 | BOSS-ONBOARD | — | — | clientStatus, onboardDate | 🧑 |

## Infrastructure Processes (Always-On, No Lead Stage)

| Process | Task | Script | Cron | What It Does |
|---------|------|--------|------|-------------|
| P15: Sync Expandi→H1 | LP-006.1 | sync-expandi-h1.js | 0 8,14,20 * * * | Sync crSent/crAccepted from Expandi to H1 |
| P16: Expandi Health | LP-006.2 | expandi-status.js | 0 */2 * * * | Monitor campaign health, alert if below target |
| P8: Metrics & Dashboard | LP-006.3 | morning-report.js | 30 7 * * * | Daily metrics summary |
| P9: Feedback Loop | LP-006.4 | (P13.4 handles pattern extraction) | — | Learn from Jamie's edits, update writing spec |
| P14: Gmail CR Pipeline | LP-006.5 | gmail-cr-pipeline.js | continuous | Real-time CR accept detection |

## Validation Gates

| Stage | Input Gate (before starting) | Output Gate (before advancing) |
|-------|----------------------------|-------------------------------|
| SOURCED | ICP criteria exist + SN access | H1 row exists with fullName + linkedinUrl |
| PROFILE_SCRAPED | linkedinUrl populated | PB profile JSON exists for lead |
| PRE_SCREENED | PB profile data exists | preScreenResult ∈ {pass, competitor, grey} |
| ACTIVITY_SCRAPED | preScreenResult = "pass" | PB activity JSON exists for lead |
| FULL_SCREENED | PB profile + activity data exist | screenResult ∈ {qualified, competitor, grey, partner} |
| INTRO_WRITTEN | screenResult = "qualified" + PB data | draft_message(J) populated + aiNotes(AJ) |
| INTRO_REVIEWED_AI | draft_message exists | aiPassed ∈ {yes, no, rewrite} |
| INTRO_REVIEWED_JAMIE | aiPassed = "yes" | jamieReviewed ∈ {approved, edited, rejected} |
| SEND_MESSAGE | jamieReviewed ∈ {approved, edited} | sendMessage column populated |
| UPLOADED_TO_EXPANDI | sendMessage populated | expandiUploaded date set |
| CR_SENT | Lead in Expandi queue | crSent(L) date set |
| CR_ACCEPTED | crSent exists | crAccepted(K) date set |
| INTRO_SENT | crAccepted + sendMessage both exist | introSent(Q) date set |
| IN_CONVERSATION | introSent exists + reply detected | conversationStatus set |
| CALL_BOOKED | Positive reply in conversation | callBooked(Y) date set |
| CALL_COMPLETED | callBooked exists + call occurred | callResult set |
| CLOSED | Successful call | dealStatus set |
| ONBOARDED | Closed deal | clientStatus = "active" |

## Mandatory Gates (Policy Enforcement)

| Gate | Rule | Blocks |
|------|------|--------|
| POL-001: Browser Tab Reuse | One tab, reuse via targetId | P5 browser ops |
| POL-002: Competitor Screen | No CRs or intros for unscreened leads | LP-003, LP-004 |
| POL-003: Account Deconfliction | No two tools on same LinkedIn account | All PB/Expandi ops |

## Neo4J Translation Guide

```cypher
// Nodes
(:Stage {name, h1Columns[], owner})
(:Task {id, name, status, owner, maturity})
(:Process {id, name, status, type})
(:Script {path, cron})
(:Skill {path})
(:H1Column {letter, name})

// Relationships
(stage)-[:PRODUCED_BY]->(process)
(task)-[:CONTAINS]->(subtask)
(task)-[:IMPLEMENTS]->(process)
(process)-[:USES_SCRIPT]->(script)
(process)-[:USES_SKILL]->(skill)
(process)-[:WRITES_TO]->(h1Column)
(stage)-[:ADVANCES_TO {type: "hard"}]->(nextStage)
(stage)-[:VALIDATES_INPUT {gate: "condition"}]->(stage)
```

## H1 Columns Needed (Gap from lead-pipeline-stages.md)

**Exist:** fullName, linkedinUrl, crSent, crAccepted, draft_message, pbProfileScrape, pbActivityScrape, aiPassed, jamieReviewed, sendMessage, introSent, ICP?(F), aiNotes(AJ), competitor_context(AK)

**Priority additions (minimum viable tracking):**
1. `pipelineStage` — single column showing current stage
2. `screenResult` — qualified/competitor/grey
3. `introWrittenDate` — when Rich wrote the intro
4. `expandiUploaded` — is this lead in Expandi?
5. `conversationStatus` — are we talking to this person?

**Full gap list:** See lead-pipeline-stages.md § "H1 Column Gap Analysis"
