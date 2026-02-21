# BC-DAILY-OUTREACH — Morning Outreach Priority Block

> **Summary:** Repeatable daily task: prioritised outreach action list via Telegram every morning. Intros, FUs, replies, pipeline hygiene — FIRST before anything else.

**Domain:** boss/lead-gen
**Priority:** 🔴 CRITICAL
**Status:** CAPTURED
**Type:** EXPLOIT
**Cat:** 🔴 A-S
**Owner:** 🔄 Hybrid
**Next Action:** Validate existing 07:30 cron (BC-067.4) delivers all 7 checklist items
**Created:** 2026-02-11
**Pipeline:** v1.1

## Win State
Every morning at 08:00, Jamie receives a prioritised Telegram action list. Each item copy-paste ready or one-tap approve. Morning outreach block completes before any other work.

## Schedule
**Daily at 08:00 GMT** (during cardio — mobile Telegram)
Rich prepares at 07:30 → delivers at 08:00

## Steps (Daily Execution)
| # | Input | Action | Output |
|---|-------|--------|--------|
| 1 | H1 (replied leads) + LinkedIn inbox | 🔴 Reply to responses | Responses sent, H1 updated |
| 2 | H1 (reviewed ✅ + passed ✅ + introSent empty) | 🟠 Send reviewed intros | Intros sent, H1 dates updated |
| 3 | H1 (draft_message + aiNotes, not reviewed) | 🟡 Review new intros (mobile-intro-review) | Intros approved/edited |
| 4 | H1 (intro sent, no reply, FU due) | 🟡 Follow-ups & ghosts (FU1 3d, FU2 5d, Ghost 5d) | FU messages sent |
| 5 | detect-new-connections output | 🟢 Check new accepts → trigger writing | New intros queued for tomorrow |
| 6 | `scripts/expandi-status.js` | 🟢 Pipeline health check | Health status |
| 7 | All above | ⚪ Log to H1 + `memory/YYYY-MM-DD.md` | Daily stats recorded |

## Output Format (Telegram)
```
☀️ Morning Outreach — [DATE]
🔴 REPLIES (X new) — [details or "None"]
🟠 READY TO SEND (X intros) — [names + links]
🟡 NEW INTROS TO REVIEW (X) — [separate messages]
🟡 FOLLOW-UPS DUE (X) — [FU details]
🟢 NEW ACCEPTS: X — [being processed]
🟢 PIPELINE: [healthy/warning] — [CRs today vs target]
```

## Dependencies / Links
- **Upstream:** BC-067 (crons power the data), BC-062 (find profiles), BC-063 (write intros), BC-052 (intro spec)
- **Downstream:** FIN-004 (daily KPIs feed from this), revenue pipeline
- **Related:** BC-INTRO-VELOCITY (velocity tracking), BC-067.4 (the cron that fires this)
- **Tools:** `skills/mobile-intro-review/`, `skills/detect-new-connections/`, `reference/intro-edit-patterns.md`, `reference/competitor-detection-criteria.md`

## Decision Log
- 2026-02-11: Created. Jamie wants this as repeatable daily block during cardio. Priority order: replies → send → review → FU → accepts → health → log.

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🔴 A-S | |
| Failure point | Initiation (Jamie must engage with morning block) | |
| Duration | 20-30min daily ⚠️ REVIEW | |
| Intervention | Restructure: Telegram delivery during cardio reduces activation energy | |
| Effectiveness | | |

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | Low | Same checklist daily |
| Procedure specification | Specified | 7-step checklist defined |
| Procedure complexity | Moderate | Multiple data sources, prioritisation |
| Temporal delay | Immediate | Do it, see results same day |
| Error cost | Moderate | Missed replies = lost hot leads |
| Reward magnitude | High | Direct revenue pipeline |
| Reward probability | Guaranteed | Completing = pipeline moves |
| Value density per unit | High | Every minute in this block is high-ROI |
| Feedback latency | Immediate | See intros sent, FUs done |
| Process legibility | Clear | Checklist with counts |
| Model maturity | Familiar | Done pattern before |
| State-tracking load | Low | Checklist resets daily |

### 0B: Channel Requirements
- **Input route:** Reading Telegram (Gc,Grw) → strong, mobile-friendly
- **Processing route:** Sequential checklist (Gsm) → structured by Rich
- **Output route:** Copy-paste + tap approve → minimal Gk
- **Channel flexible:** N — must be Telegram during cardio
- **Mismatch flags:** Gs (speed) mitigated by copy-paste ready format

### 0C: Affective Load
| Dimension | Present | Intensity |
|-----------|---------|-----------|
| Interpersonal risk | Y | Low — sending messages to strangers |
| Status challenge | N | — |
| Exposure / visibility | Y | Low — LinkedIn DMs |
| Uncertain return | Y | Low — some won't reply |
| Confrontation potential | N | — |
| Identity-relevant outcome | Y | Low — "am I a salesperson?" |

### Layer 3 Computation
- **Epistemic value:** None (routine)
- **Pragmatic value:** Very high (direct revenue)
- **Effort cost:** Low (Rich prepares everything)
- **Threat:** Low (mild A-S, well-structured)
- **Dominant signal:** → 🔴 A-S (mild aversion, fully structurable)

### Predicted Failure Point
- **Stage:** Initiation
- **Cause:** Morning resistance, other priorities feel more urgent
- **Auto-intervention:** Telegram push during cardio — zero activation energy

### Intervention Stack (if B/A)
- **Drivers:** Mild interpersonal risk, identity relevance
- **Stack:** Pre-built checklist (zero creation), cardio timing (DA boost), copy-paste format
- **Confidence:** PRELIMINARY
- **Conflicts checked:** N

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-11 | Initial creation | Rich |
| 1.1 | 2026-02-21 | Reformatted to v1.1 template (RTP candidate) | Atlas |
