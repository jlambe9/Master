# CLAWD-003 — Live Business Dashboard (Trading Screen)

> **Summary:** Trading-screen-style business dashboard — always visible, real-time, mobile + web. Revenue health bar, KPI pips, cron status, pipeline funnel.

**Domain:** clawd/integrations
**Priority:** 🟡 HIGH
**Status:** CAPTURED
**Type:** EXPLOIT
**Cat:** 🟢 E
**Owner:** 🤖 Rich
**Next Action:** Design data schema — which APIs/sources feed each widget
**Created:** 2026-02-12
**Pipeline:** v1.2

## Win State
Live dashboard showing: revenue progress bar, daily KPI pips (streak tracker), cron status panel, current task, pipeline funnel. Auto-refreshing, mobile-accessible.
**Outputs (completion gate — ALL must exist to mark done):**
1. Live dashboard accessible on mobile + web
2. Revenue health bar, KPI pips, cron status panel, pipeline funnel visible
3. Auto-refreshing with real data

## Layout
- **Top Bar:** Revenue health bar (£ actual vs £5K target, color-coded)
- **KPI Pips:** Daily rows for CRs sent, accepts, intros, replies, calls, revenue (pip per day)
- **Cron Panel:** Every cron/daemon with 🟢🟡🔴 status, last/next run
- **Task Panel:** Active task, time on task, subtask progress
- **Pipeline Funnel:** Leads → CRs → Accepts → Intros → Replies → Calls → Clients with conversion rates

## Data Sources
| Widget | Source |
|--------|--------|
| Revenue bar | Manual input or Stripe (future) |
| KPI pips | H1 sheet (daily counts by date) |
| Cron status | Clawdbot cron API / state files |
| Current task | ~/Master/STATUS.md |
| Pipeline funnel | H1 sheet (stage counts) |
| Expandi stats | Expandi API / `scripts/expandi-status.js` |

## Dependencies / Links
- **Upstream:** BC-058 (pipeline tracking — overlaps), BC-067 (cron data source), H1 sheet
- **Downstream:** FIN-004 (KPIs visualised here)
- **Related:** BC-DAILY-OUTREACH (morning briefing could link to dashboard)

## Decision Log
- 2026-02-12: Jamie described vision — trading screen with health bars, KPI pips, cron status. Mobile-first, always accessible.

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🟢 E | |
| Failure point | Decomposition (many widgets) | |
| Duration | 8h ⚠️ REVIEW | |
| Intervention | None (E-task for Rich) | |
| Effectiveness | | |

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | Med | Known pattern, novel integration |
| Procedure specification | Partial | Vision clear, build details TBD |
| Procedure complexity | Complex | Multiple data sources, real-time |
| Temporal delay | Days | Build + deploy cycle |
| Error cost | Reversible | Can iterate freely |
| Reward magnitude | Med | Visibility, not direct revenue |
| Reward probability | Guaranteed | Will produce a dashboard |
| Value density per unit | High | Fun build work |
| Feedback latency | Immediate | See dashboard live |
| Process legibility | Clear | Visual output |
| Model maturity | Familiar | Dashboard pattern known |
| State-tracking load | Med | Multiple widgets |

### 0B: Channel Requirements
- **Input route:** API docs + data schemas (Gc,Grw) → Rich
- **Processing route:** Systems integration (Gf,Gwm) → Rich
- **Output route:** Code (HTML/JS) → Rich
- **Channel flexible:** N/A — Rich autonomous
- **Mismatch flags:** None

### 0C: Affective Load
All dimensions: N / —

### Layer 3 Computation
- **Epistemic value:** Medium (novel integration)
- **Pragmatic value:** Medium (visibility tool)
- **Effort cost:** Medium
- **Threat:** None
- **Dominant signal:** → 🟢 E (fun build, SEEKING-compatible)

### Predicted Failure Point
- **Stage:** Decomposition (too many widgets)
- **Cause:** Scope creep
- **Auto-intervention:** MVP with 3 widgets, add rest iteratively

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-12 | Initial creation | Rich |
| 1.1 | 2026-02-21 | Reformatted to v1.1 template | Atlas |
