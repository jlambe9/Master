# Lead Pipeline Stages — Full Map

*Each stage a lead passes through from sourcing to revenue.*
*Each stage has: Input → Process → Output → H1 field → Status values → RTP reference*
*This is the source of truth for what H1 needs to track.*

## Pipeline Overview

```
SOURCED → PROFILE_SCRAPED → PRE_SCREENED → ACTIVITY_SCRAPED → FULL_SCREENED → 
INTRO_WRITTEN → INTRO_REVIEWED_AI → INTRO_REVIEWED_JAMIE → 
UPLOADED_TO_EXPANDI → CR_SENT → CR_ACCEPTED → INTRO_SENT → 
IN_CONVERSATION → CALL_BOOKED → CALL_COMPLETED → CLOSED → ONBOARDED
```

## Stage Detail

### 1. SOURCED
- **Input:** ICP criteria + Sales Navigator search
- **Process:** Export leads from SN → deduplicate against H1
- **Output:** Lead row in H1 with name + LinkedIn URL
- **H1 field:** `pipelineStage` = "sourced" (or row exists = sourced)
- **H1 columns needed:** `fullName`, `linkedinUrl`, `sourceDate`, `sourceBatch`
- **Existing?** fullName ✅, linkedinUrl ✅, sourceDate ❌, sourceBatch ❌
- **RTP:** skills/pb-profile-scraper (upstream of this — SN export is manual)

### 2. PROFILE_SCRAPED
- **Input:** LinkedIn URL
- **Process:** PB Profile Scraper → bio, headline, experience, groups
- **Output:** PB profile JSON + H1 flag
- **H1 field:** `pbProfileScrape` = date scraped (or true/false)
- **H1 columns needed:** `pbProfileScrape` (date), `headline`, `bio` (summary)
- **Existing?** pbProfileScrape ✅, headline ❌ (in PB data but not H1), bio ❌
- **RTP:** skills/pb-profile-scraper/SKILL.md

### 3. PRE_SCREENED
- **Input:** PB profile data (headline, bio, experience)
- **Process:** Auto pre-filter against competitor-detection-criteria.md
- **Output:** ICP classification (Yes/No/Grey)
- **H1 field:** `preScreenResult` = "pass" | "competitor" | "grey"
- **H1 columns needed:** `preScreenResult`, `preScreenDate`
- **Existing?** `passed?` exists but unclear if this is pre-screen or full screen ❌
- **RTP:** BC-065.2 (auto pre-filter — TODO)

### 4. ACTIVITY_SCRAPED
- **Input:** LinkedIn URL (pre-screened leads only)
- **Process:** PB Activity Extractor → posts, comments, reactions
- **Output:** PB activity JSON + H1 flag
- **H1 field:** `pbActivityScrape` = date scraped
- **H1 columns needed:** `pbActivityScrape` (date), `activitySummary` (key themes)
- **Existing?** pbActivityScrape ✅, activitySummary ❌
- **RTP:** skills/pb-activity-extractor/SKILL.md

### 5. FULL_SCREENED
- **Input:** Profile data + activity data
- **Process:** Full competitor screen + intent scoring
- **Output:** Final qualification (Qualified/Competitor/Grey/Partner)
- **H1 field:** `screenResult` = "qualified" | "competitor" | "grey" | "partner"
- **H1 columns needed:** `screenResult`, `screenDate`, `screenNotes`, `problemTags` (explicit/implicit/situational)
- **Existing?** `passed?` might be this ❌ (ambiguous), `competitor_context` exists for grey/competitor
- **RTP:** skills/competitor-screen/SKILL.md

### 6. INTRO_WRITTEN
- **Input:** Profile + activity data + intro-writing-spec.md
- **Process:** Write personalized intro message
- **Output:** Draft intro in H1
- **H1 field:** `draft_message` = the intro text
- **H1 columns needed:** `draft_message`, `introWrittenDate`, `aiNotes` (context for references)
- **Existing?** draft_message ✅, introWrittenDate ❌, aiNotes ✅
- **RTP:** skills/write-intro-messages/SKILL.md

### 7. INTRO_REVIEWED_AI
- **Input:** Draft intro
- **Process:** AI self-review — name validation, must-have/must-not, quality check
- **Output:** Pass/fail + issues flagged
- **H1 field:** `aiReviewResult` = "pass" | "fail" | "rewrite"
- **H1 columns needed:** `aiReviewResult`, `aiReviewDate`, `aiReviewNotes`
- **Existing?** ❌ (currently no AI review step tracked)
- **RTP:** Part of write-intro-messages skill (needs extraction as separate step)

### 8. INTRO_REVIEWED_JAMIE
- **Input:** AI-passed intro
- **Process:** Jamie reviews on mobile (skills/mobile-intro-review)
- **Output:** Approved / Edit / Reject
- **H1 field:** `jamieReviewResult` = "approved" | "edited" | "rejected"
- **H1 columns needed:** `jamieReviewResult`, `jamieReviewDate`
- **Existing?** `reviewed` column exists but meaning unclear ❌
- **RTP:** skills/mobile-intro-review/SKILL.md

### 9. UPLOADED_TO_EXPANDI
- **Input:** Approved intro + LinkedIn URL
- **Process:** Generate CSV with profile_link + custom_message → import to Expandi
- **Output:** Lead in Expandi campaign with message placeholder
- **H1 field:** `expandiUploaded` = date uploaded
- **H1 columns needed:** `expandiUploaded`, `expandiBatch`, `expandiCampaign`
- **Existing?** ❌ (no upload tracking)
- **RTP:** BC-065.3 (CSV generator — TODO)

### 10. CR_SENT
- **Input:** Lead in Expandi queue
- **Process:** Expandi sends CR automatically
- **Output:** CR sent confirmation
- **H1 field:** `crSent` = date sent
- **H1 columns needed:** `crSent` (date)
- **Existing?** crSent ✅
- **RTP:** Expandi automated

### 11. CR_ACCEPTED
- **Input:** CR sent
- **Process:** Lead accepts (Gmail notification or Expandi sync)
- **Output:** Connection established
- **H1 field:** `crAccepted` = date accepted
- **H1 columns needed:** `crAccepted` (date)
- **Existing?** crAccepted ✅
- **RTP:** skills/detect-new-connections/ + sync-expandi-h1

### 12. INTRO_SENT
- **Input:** Accepted connection + approved intro
- **Process:** Auto-send via Expandi placeholder OR manual paste
- **Output:** First message delivered
- **H1 field:** `introSent` = date sent
- **H1 columns needed:** `introSent` (date), `introSentMethod` (auto/manual)
- **Existing?** introSent ✅, introSentMethod ❌
- **RTP:** Expandi auto-send or manual

### 13. IN_CONVERSATION
- **Input:** Intro sent
- **Process:** Lead replies → conversation begins
- **Output:** Active conversation
- **H1 field:** `conversationStatus` = "replied" | "ghosted" | "active" | "nurture"
- **H1 columns needed:** `firstReplyDate`, `conversationStatus`, `lastMessageDate`
- **Existing?** ❌ (no conversation tracking)
- **RTP:** BC-065.5 (reply detection — TODO)

### 14. CALL_BOOKED
- **Input:** Active conversation
- **Process:** Lead books call (Calendly or direct)
- **Output:** Calendar event
- **H1 field:** `callBooked` = date/time of call
- **H1 columns needed:** `callBooked`, `callDate`
- **Existing?** ❌
- **RTP:** BOSS-SALES (TODO)

### 15. CALL_COMPLETED
- **Input:** Booked call
- **Process:** Sales call (Sandler framework)
- **Output:** Call notes + outcome
- **H1 field:** `callResult` = "closed" | "follow-up" | "not-fit" | "no-show"
- **H1 columns needed:** `callResult`, `callDate`, `callNotesLink`
- **Existing?** ❌
- **RTP:** BC-CALL-NOTES + BC-PRECALL-PREP

### 16. CLOSED
- **Input:** Successful call
- **Process:** Payment received
- **Output:** Paying client
- **H1 field:** `dealStatus` = "closed" | "lost"
- **H1 columns needed:** `dealStatus`, `dealDate`, `dealValue`, `paymentReceived`
- **Existing?** ❌
- **RTP:** BOSS-SALES (TODO)

### 17. ONBOARDED
- **Input:** Closed deal
- **Process:** Onboarding flow (BOSS-ONBOARD)
- **Output:** Active client
- **H1 field:** `clientStatus` = "onboarding" | "active" | "churned"
- **H1 columns needed:** `clientStatus`, `onboardDate`, `programStartDate`
- **Existing?** ❌
- **RTP:** BOSS-ONBOARD (TODO)

---

## H1 Column Gap Analysis

### Currently Exist (10 columns):
fullName, linkedinUrl, crSent, crAccepted, draft_message, pbProfileScrape, pbActivityScrape, reviewed, passed?, introSent

### Need Adding (28 columns):
sourceDate, sourceBatch, headline, bio, preScreenResult, preScreenDate, activitySummary, screenResult, screenDate, screenNotes, problemTags, introWrittenDate, aiReviewResult, aiReviewDate, aiReviewNotes, jamieReviewResult, jamieReviewDate, expandiUploaded, expandiBatch, expandiCampaign, introSentMethod, firstReplyDate, conversationStatus, lastMessageDate, callBooked, callDate, callResult, callNotesLink, dealStatus, dealDate, dealValue, paymentReceived, clientStatus, onboardDate, programStartDate

### Need Clarifying (2 columns):
- `reviewed` — what does this currently mean? Pre-screen? Jamie review? AI review?
- `passed?` — pre-screen or full screen? What values?

### Priority (what to add FIRST for minimum viable pipeline tracking):
1. `pipelineStage` — single column showing current stage (sourced → closed)
2. `screenResult` — qualified/competitor/grey (replace ambiguous `passed?`)
3. `introWrittenDate` — when Rich wrote the intro
4. `jamieReviewResult` — approved/edited/rejected
5. `expandiUploaded` — is this lead in Expandi?
6. `conversationStatus` — are we talking to this person?

These 6 columns give us end-to-end pipeline visibility. The rest can be added incrementally.
