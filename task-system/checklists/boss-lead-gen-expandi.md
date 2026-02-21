# Expandi Upstream Checklist — "What to check when Expandi stops"

*Full flow from leads to active campaign. Check in order. First failure = root cause.*

## Pipeline Flow (check in order)

### 1. Lead Source
- [ ] ICP criteria defined (`reference/icp-criteria.md`)
- [ ] Lead list sourced (Sales Navigator / other)
- [ ] Leads deduplicated against H1 existing contacts

### 2. Lead Validation (PB Profile Scraper)
- [ ] PhantomBuster cookies valid (check PB dashboard)
- [ ] Profile Scraper agent configured
- [ ] Profiles scraped → JSON output exists
- [ ] Data quality check: headline, bio, experience populated

### 3. Pre-Screen (Competitor Filter)
- [ ] Auto pre-filter script run (BC-065.2)
- [ ] Competitors flagged (ICP?=No in H1)
- [ ] Grey leads flagged for Jamie review
- [ ] Clean leads marked for next stage

### 4. Activity Scrape (PB Activity Extractor)
- [ ] PB Activity Extractor cookies valid
- [ ] Activity data scraped for clean leads
- [ ] Posts/comments/reactions captured
- [ ] Data merged with profile data

### 5. Full Screen + Intent Scoring
- [ ] Competitor screen complete (`skills/competitor-screen/`)
- [ ] Problem indicators tagged (explicit/implicit/situational)
- [ ] Final qualified lead list produced

### 6. Intros Written
- [ ] Intro writing skill functional (`skills/write-intro-messages/`)
- [ ] Intros written for all qualified leads
- [ ] AI notes (column AJ) populated for every specific reference
- [ ] Competitor context (column AK) populated for grey/competitor leads

### 7. Intros Reviewed
- [ ] AI self-review: name validation, must-have/must-not checks passed
- [ ] Jamie mobile review: hook quality, personalisation accuracy
- [ ] Rejected intros flagged for rewrite
- [ ] Approved intros in H1 column J (draft_message)

### 8. Expandi Upload
- [ ] CSV generated with profile_link + custom_message placeholder (BC-065.3)
- [ ] CSV imported into Expandi campaign
- [ ] Placeholder rendering verified (test with 1 lead)
- [ ] Auto-send on accept configured

### 9. Campaign Active
- [ ] Expandi session connected (not expired)
- [ ] Campaign status = ACTIVE
- [ ] Daily CR limit set (35/day)
- [ ] Queue populated (leads loaded)
- [ ] Sending hours configured (05:30-21:30 GMT)
- [ ] No LinkedIn restrictions on account

### 10. Monitoring
- [ ] Expandi health check cron running (every 2h)
- [ ] Gmail CR pipeline active (acceptance detection)
- [ ] Sync Expandi→H1 cron running (every 3h)
- [ ] Reply detection active (BC-065.5 — TODO)

## Access Validation
When debugging, verify in this order:
1. **Browser control** → can Rich open app.expandi.io via clawd profile?
2. **Expandi API** → does `node scripts/expandi-status.js` return data?
3. **PhantomBuster API** → are agents accessible?
4. **H1 Sheet API** → can scripts read/write?
5. **Gmail** → is IMAP/polling functional?

## Quick Triage: Resume vs Rebuild

Before walking the full pipeline, determine which situation you're in:

**RESUME (campaign was working, now stopped):**
- Check step 9 FIRST: Is campaign active? Session connected? Queue populated?
- If just deactivated/expired → reactivate → done
- If session disconnected → reconnect in Expandi dashboard → reactivate
- If queue empty but leads remain → check campaign settings, daily limits, schedule

**REBUILD (new batch of leads needed):**
- Walk steps 1-8 in order: source → validate → screen → scrape → screen → write → review → upload
- First unchecked item = where to start

## When This Checklist Fires
- Expandi health check returns INACTIVE or 0 CRs
- Daily template scan detects lead-gen domain issues
- Manual trigger: "why isn't outreach working?"

Walk the checklist top to bottom. First unchecked item = root cause.
