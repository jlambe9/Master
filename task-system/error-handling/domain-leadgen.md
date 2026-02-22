# Domain Error Playbook — Lead Gen

Known lead generation pipeline error patterns and resolutions. These are business logic failures specific to the LinkedIn outreach domain, not tool failures (those are in tool-errors.md).

---

**Error: Lead has no LinkedIn headline — intro writing fails**
- Pattern: Intro writing process reads lead profile, headline field is empty. Can't write personalised hook without headline context.
- Likely cause: (a) Profile was private when scraped. (b) PhantomBuster didn't capture headline. (c) Lead changed their profile after scraping.
- Resolution: (1) Check if profile is accessible — open LinkedIn URL. (2) If accessible: re-scrape with PB profile scraper. (3) If private: skip lead, mark as INSUFFICIENT_DATA in H1. (4) If headline exists but wasn't captured: fix scraper field mapping.
- Prevention: Profile scraper validation step — flag leads with missing headline before they enter intro writing queue.
- Severity: 🟢 Cosmetic (one lead skipped, pipeline continues)
- First seen: 2026-02-04 — multiple leads with empty headlines during batch intro writing

---

**Error: Lead is actually a competitor (sells ADHD/wellness solutions)**
- Pattern: Intro sent to someone who turns out to be a competitor — they sell similar services, not someone who experiences the problems we solve. Wastes a connection and potentially alerts competition.
- Likely cause: Screening didn't catch them. ICP filter too broad. Lead's headline is ambiguous (e.g. "ADHD Coach" could be competitor or person with ADHD who coaches in another domain).
- Resolution: (1) Mark screenResult=competitor in H1. (2) Do NOT send intro. (3) If intro already sent, do not follow up. (4) Review screening criteria for the pattern that missed this.
- Prevention: competitor-screen skill runs BEFORE intro writing. Check for: sells coaching/consulting, has "coach" in title with wellness/ADHD qualifier, company is in ADHD/wellness space.
- Severity: 🟡 Degrades system (wasted connection, minor risk)
- First seen: Anticipated — screening process designed to prevent this

---

**Error: Intro written but sendMessage column empty**
- Pattern: Intro exists in draft_message column but sendMessage (the canonical final message) is empty. If auto-send is configured, nothing gets sent.
- Likely cause: Intro was written to draft_message but never approved/moved to sendMessage. The H1 pipeline has a deliberate separation: draft_message is the draft, sendMessage is the approved final version. Never send from draft_message.
- Resolution: (1) Check if intro was reviewed (jamieReviewed column). (2) If reviewed and approved: copy draft_message → sendMessage. (3) If not reviewed: add to review queue. (4) NEVER auto-copy draft to sendMessage without review.
- Prevention: Pipeline enforces: draft_message → Jamie reviews → sendMessage populated. Intro catchup cron reports leads stuck with draft but no sendMessage.
- Severity: 🟡 Degrades system (intros don't get sent, throughput drops)
- First seen: 2026-02-21 — H1 column confusion between draft and final

---

**Error: Lead accepted CR but profile now private/deleted**
- Pattern: Lead accepted connection request. Intro is ready to send. But LinkedIn profile is now inaccessible — private, deleted, or suspended.
- Likely cause: Lead changed privacy settings, deactivated account, or was suspended by LinkedIn.
- Resolution: (1) Mark lead as DEAD in H1. (2) Do not attempt to send intro. (3) Remove from active pipeline. (4) Don't count against daily send targets.
- Prevention: Before sending intro, verify profile is accessible. Add a "profile check" step before send.
- Severity: 🟢 Cosmetic (one lead lost, pipeline continues)
- First seen: Anticipated — natural attrition in any outreach pipeline

---

**Error: Daily CR volume consistently below target**
- Pattern: CRs sent per day consistently below 35+ target. Pipeline throughput insufficient to feed mechanism chain.
- Likely cause: (a) Expandi campaign limits set too low. (b) Search list exhausted — no more leads matching criteria. (c) LinkedIn throttling due to account age/warmup. (d) Campaign paused/inactive (see tool-errors.md Expandi entry). (e) New batch of leads needed.
- Resolution: (1) Check Expandi dashboard — campaign limits, daily sends. (2) Check search list size — how many leads remaining? (3) If list exhausted: source new batch (LP-001 task). (4) If throttled: check warmup settings, may need to increase gradually. (5) If limits too low: increase in Expandi settings (max safe: 40-50/day for warmed account).
- Prevention: Weekly outreach report (part of weekly review prep) tracks volume vs target. Morning briefing flags if yesterday's CRs were below target.
- Severity: 🟡 Degrades system (M1 throughput drops, goal timeline extends)
- First seen: 2026-02-14 — 0 CRs for 8+ days due to inactive campaign

---

**Error: Agent gives up on first failure instead of trying alternatives**
- Pattern: Agent hits a tool error (browser timeout, API failure) and immediately reports "couldn't do it" to Jamie. Doesn't retry, doesn't try alternative tools, doesn't debug, doesn't check the error playbook.
- Likely cause: No explicit rule requiring alternative attempts before reporting failure. Agent defaults to the path of least resistance (report and wait).
- Resolution: This is a behavioural pattern, not a single incident. The fix is the "try before you fail" rule in AGENTS.md error handling protocol: (1) retry after 30 seconds, (2) try different tool for same job, (3) debug the failing tool, (4) spawn sub-agent to attempt differently, (5) check error playbook. Only after exhausting alternatives → escalate.
- Prevention: AGENTS.md error handling protocol (#55) includes the "try before you fail" rule. Every cron prompt includes error handling instructions.
- Severity: 🟡 Degrades system (work stalls unnecessarily, Jamie pulled into things Rich could solve)
- First seen: Multiple — ongoing pattern throughout 2026-02
