# BC-INTRO-VELOCITY — Maximum Intro Sending Velocity

> **Summary:** Write, validate, and send intros to ALL current CR accepts. Clear the backlog, then keep pace with new accepts.

**Domain:** boss/lead-gen
**Priority:** 🔴 CRITICAL
**Status:** IN PROGRESS
**Type:** EXPLOIT
**Cat:** 🔴 A-S
**Owner:** 🔄 Hybrid
**Next Action:** Jamie sends the 8 ready intros (ST-0), Rich validates 13 existing intros (ST-1)
**Created:** 2026-02-11
**Pipeline:** v1.1

## Win State
Every CR-accepted lead has a validated intro with aiNotes, reviewed by Jamie, and sent. Zero backlog. New accepts get intros within 24h.

## Current Pipeline Numbers (2026-02-11 16:49)
| Stage | Count | Action |
|-------|-------|--------|
| Ready to send (reviewed) | 8 | Jamie sends |
| Written + edited | 2 | Final review → send |
| Awaiting Jamie's review | 2 | Jamie reviews |
| Written, no context | 13 | ST-1: Validate + add aiNotes |
| CR accepted, no intro (customers) | ~21 | ST-2: Write from scratch |
| CR accepted, no intro (grey area) | ~8 | ST-3: Jamie decides |
| CR sent, awaiting accept | 59 | ST-4: Write as they accept |

## Steps
| # | Input | Action | Output |
|---|-------|--------|--------|
| 0 | 8 ready intros in H1 | Jamie copies from H1 col L → sends via LinkedIn DM | 8 intros sent, H1 updated |
| 1 | 13 intros with draft_message but no aiNotes | Rich validates against updated process + adds aiNotes | 13 intros ready for Jamie review |
| 2 | 21 accepted customers with no intro | Rich writes full intros: PB → screen → write → aiNotes | 21 intros ready for review |
| 3 | 8 grey area leads | Jamie decides: partner/customer/exclude per lead | Classification decisions |
| 4 | New accepts (ongoing) | Rich monitors + auto-writes within 24h | Continuous pipeline |
| 5 | Automatable? | Investigate Expandi send vs manual LinkedIn DM | Send automation decision |

## Subtasks
| # | Type | Task | Status | Owner | Notes |
|---|------|------|--------|-------|-------|
| ST-0 | EXPLOIT | Send 8 ready intros | CAPTURED | 🧑 Jamie | Rows 3,4,5,14,15,22,26,27 |
| ST-1 | EXPLOIT | Validate 13 + add aiNotes | CAPTURED | 🤖 Rich | ~30min sub-agent |
| ST-2 | EXPLOIT | Write 21 new intros | CAPTURED | 🤖 Rich | ~45min sub-agent |
| ST-3 | EXPLOIT | Decide 8 grey area leads | CAPTURED | 🧑 Jamie | ADHD product builders |
| ST-4 | EXPLOIT | Real-time accept monitoring | IN PROGRESS | 🤖 Rich | BC-065 / daily catch-up |
| ST-5 | EXPLORE | Investigate send automation | CAPTURED | 🤖 Rich | Expandi vs manual |

## Dependencies / Links
- **Upstream:** BC-052 (intro spec), BC-062 (find profiles), BC-057 (Expandi generating CRs)
- **Downstream:** BC-DAILY-OUTREACH (morning send list), revenue pipeline
- **Related:** BC-063 (standard intro writing), BC-065 (pipeline v2 eliminates backlog permanently)
- **Tools:** H1 Google Sheet, `reference/intro-edit-patterns.md`, `reference/competitor-detection-criteria.md`

## Decision Log
- 2026-02-11: Created. Backlog: 8 ready, 13 need validation, 21 need writing. Priority is velocity — clear then maintain pace.

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🔴 A-S | |
| Failure point | Initiation (Jamie sending) | |
| Duration | 3-5 days to clear backlog ⚠️ REVIEW | |
| Intervention | Batch in morning outreach block | |
| Effectiveness | | |

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | Low | Known process, clear numbers |
| Procedure specification | Specified | Process documented |
| Procedure complexity | Moderate | Multiple subtasks, staging |
| Temporal delay | Days | Backlog clear over days |
| Error cost | Moderate | Bad intros waste leads |
| Reward magnitude | High | Direct pipeline revenue |
| Reward probability | Guaranteed | Sending = done |
| Value density per unit | High | Each intro = potential client |
| Feedback latency | Delayed | Reply rate over days |
| Process legibility | Clear | Numbered backlog counts |
| Model maturity | Familiar | Intro writing process known |
| State-tracking load | Med | Track per-profile status |

### 0B: Channel Requirements
- **Input route:** H1 data (Rich reads) → Jamie reads Telegram review
- **Processing route:** Rich writes (Gc) → Jamie reviews (Gc,Gf)
- **Output route:** Jamie copy-paste sends (minimal Gk)
- **Channel flexible:** Partially — review on mobile, send must be LinkedIn
- **Mismatch flags:** Gs if many intros to send manually

### 0C: Affective Load
| Dimension | Present | Intensity |
|-----------|---------|-----------|
| Interpersonal risk | Y | Low — sending to strangers |
| Status challenge | N | — |
| Exposure / visibility | Y | Low — LinkedIn DMs |
| Uncertain return | Y | Low — reply rate uncertain |
| Confrontation potential | N | — |
| Identity-relevant outcome | Y | Low — "am I salesy?" |

### Layer 3 Computation
- **Epistemic value:** None
- **Pragmatic value:** Very high
- **Effort cost:** Low (Rich does heavy lifting)
- **Threat:** Low (mild aversion, structured)
- **Dominant signal:** → 🔴 A-S (mild aversion, fully structurable via morning block)

### Predicted Failure Point
- **Stage:** Initiation (Jamie sending)
- **Cause:** Competes with more interesting tasks
- **Auto-intervention:** Embed in morning outreach block (BC-DAILY-OUTREACH)

### Intervention Stack (if B/A)
- **Drivers:** Mild interpersonal risk, identity relevance
- **Stack:** Morning block timing, copy-paste format, batch sending
- **Confidence:** PRELIMINARY
- **Conflicts checked:** N

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-11 | Initial creation | Rich |
| 1.1 | 2026-02-21 | Reformatted to v1.1 template | Atlas |
