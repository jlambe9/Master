# Tool Error Playbook

Known external tool error patterns and resolutions. Add new entries as errors are encountered.

---

**Error: Expandi campaign inactive / no CRs sending**
- Pattern: Daily CR count drops to 0. Expandi health check reports INACTIVE. Can persist for days unnoticed if health check isn't actioned.
- Likely cause: (a) Expandi session disconnected (LinkedIn logged out). (b) Campaign manually paused. (c) Warmup mode throttling to zero. (d) Daily limit reached and not reset. (e) Account flagged by LinkedIn.
- Resolution: (1) Go to app.expandi.io → check campaign status. (2) Check session status — if disconnected, reconnect LinkedIn session. (3) Check warmup settings — if throttled, adjust. (4) Check daily limits — if at zero, investigate why. (5) If account flagged → stop all campaigns, wait 48h, restart slowly.
- Prevention: Expandi health cron checks every 2h. BUT the cron must be ACTIONED — just alerting isn't enough. If alert fires 3 times with no response, escalate severity.
- Severity: 🔴 Blocks system (M1 pipeline stops entirely)
- First seen: 2026-02-14 — campaign inactive for 8+ days before anyone noticed, despite health check existing

---

**Error: Expandi step delays wrong — campaign flagged by LinkedIn**
- Pattern: Campaign sends CRs too fast. LinkedIn throttles or flags the account. CR acceptance rate drops sharply.
- Likely cause: Campaign created with default delays (too short). LinkedIn detects automated behaviour.
- Resolution: (1) Pause campaign immediately. (2) Create new campaign with 2-5 minute delays between steps. (3) Wait 24-48h before restarting. (4) Monitor first 50 CRs closely.
- Prevention: All new campaigns must use 2-5 min delays. Documented in expandi-campaign-setup skill.
- Severity: 🔴 Blocks system (account risk)
- First seen: 2026-02-04 — delays too short, had to recreate campaign

---

**Error: H1 sync column mapping wrong**
- Pattern: Data appears in wrong H1 columns. Intro messages in wrong field. Statuses not updating correctly.
- Likely cause: H1 sheet structure changed (columns added/moved) but sync script still uses old column indices.
- Resolution: (1) Open H1 sheet, verify current column structure. (2) Compare against sync script column mappings. (3) Update mappings to match current sheet. (4) Re-run sync to verify.
- Prevention: Sync script should read column headers not indices. If using indices, document expected structure and validate before writing.
- Severity: 🟡 Degrades system (bad data, intros sent to wrong people)
- First seen: 2026-02-03 — was using wrong columns after sheet restructure

---

**Error: Browser control service timeout**
- Pattern: Browser action (snapshot, navigate, act) returns timeout error. Agent reports "browser not available."
- Likely cause: (a) clawd browser profile not running. (b) CDP port 18800 not responding. (c) Browser process crashed. (d) Page is slow loading / infinite redirect.
- Resolution: (1) Check browser status: `browser status`. (2) If not running: `browser start`. (3) If running but unresponsive: `browser stop` then `browser start`. (4) If page issue: try navigating to a simple page first to verify browser works, then retry original page. (5) If still broken: check CDP port in config (should be 18800).
- Prevention: System health cron could include browser status check. Before browser-dependent tasks, verify browser is running.
- Severity: 🟡 Degrades system (automation tasks fail, manual fallback needed)
- First seen: 2026-02-22 — timeout on Expandi health check browser snapshot

---

**Error: PhantomBuster scraper tab accumulation / 404s**
- Pattern: Browser becomes slow or unresponsive during PB scraping. Multiple tabs open. Some LinkedIn profiles return 404.
- Likely cause: Script opens new tabs for each profile but doesn't close them. Some LinkedIn URLs are stale (profile deleted/renamed).
- Resolution: (1) Kill excess tabs. (2) Implement tab management in scraper script (close tab after scraping). (3) Skip 404 URLs — mark as DEAD in lead list, don't retry.
- Prevention: Scraper script must close tabs after each profile. Add 404 detection and skip logic.
- Severity: 🟡 Degrades system (scraping stalls)
- First seen: 2026-02-04 — tab accumulation during batch scrape

---

**Error: Brave Search API key missing**
- Pattern: Web search returns error or empty results. Agent reports search unavailable.
- Likely cause: API key not configured in OpenClaw environment.
- Resolution: (1) Check if key exists: look in OpenClaw config env section. (2) If missing: Jamie needs to add Brave Search API key. (3) Add to config: `gateway config.patch` with env.BRAVE_API_KEY.
- Prevention: Global infra checklist includes API key verification.
- Severity: 🟡 Degrades system (research tasks fail, agent can use alternative search methods)
- First seen: 2026-02-21 — search tasks failing silently
