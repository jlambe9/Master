# CLAWD-003: Live Business Dashboard (Trading Screen)

**Status:** CAPTURED
**Priority:** 🟡 HIGH
**Type:** EXPLOIT
**Domain:** clawd/integrations

## Vision
A trading-screen-style business dashboard — always visible, real-time, mobile + web. Think Bloomberg terminal meets gaming HUD for a one-person business.

## Layout Concept

### Top Bar: North Star Health Bar
- Revenue progress toward current target (£5K/mo)
- Visual loading bar showing actual revenue vs target
- Color-coded: red (<30%), yellow (30-70%), green (>70%)
- Updates in real-time as clients close

### KPI Pips (daily rows)
- Each major KPI has a row of "pips" (one per day, Mon-Sun)
- Pip fills/lights up when that day's KPI is hit
- Like a streak tracker or achievement bar
- KPIs:
  - CRs sent (target: 35/day)
  - Accepts received
  - Intros sent
  - Replies received
  - Calls booked
  - Revenue closed

### Cron Status Panel
- Every cron/daemon with live status indicator
  - 🟢 Running / last fired OK
  - 🟡 Warning (late, partial)
  - 🔴 Failed / down
- Last run time, next run time
- Click to see last output

### Current Task Panel
- Active task from PLAN.md / Master STATUS.md
- Time on task
- Subtask progress

### Upcoming Tasks
- Next 3-5 tasks in priority order
- Due dates / blockers

### Pipeline Funnel Visual
- Leads → CRs → Accepts → Intros → Replies → Calls → Clients
- Numbers at each stage, conversion rates between
- Live data from H1

## Technical Approach
- **Frontend:** Single HTML page, dark theme, responsive (mobile-first)
- **Data:** Pulls from Google Sheets API (H1), Expandi API, cron state files, Master repo
- **Hosting:** Cloudflare Pages (free, always accessible) or local + Tailscale
- **Refresh:** Auto-refresh every 60 seconds, or websocket for true real-time
- **Auth:** Simple token or IP-restricted

## Data Sources
| Widget | Source |
|--------|--------|
| Revenue bar | Manual input or Stripe (future) |
| KPI pips | H1 sheet (daily counts by date) |
| Cron status | Clawdbot cron API / state files |
| Current task | ~/Master/STATUS.md |
| Pipeline funnel | H1 sheet (stage counts) |
| Expandi stats | Expandi API / scripts/expandi-status.js |

## Decision Log
- 2026-02-12: Jamie described vision — trading screen with health bars, KPI pips, cron status, task tracking. Mobile-first, always accessible. Filed as CLAWD-003.
