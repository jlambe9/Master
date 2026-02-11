# BC-PRECALL-PREP — Sales Call Prep Skill (Sandler Framework)

> **Summary:** Create a skill that auto-generates a Sandler-structured call plan when a sales call is booked. Pulls all available data and identifies information gaps + questions to fill them.

**Domain:** boss/sales
**Priority:** 🔴 CRITICAL
**Status:** CAPTURED
**Type:** EXPLOIT
**Cat:** 🔴 A-S (revenue-critical)
**Created:** 2026-02-11
**Depends on:** BC-OFFER-V1 (offer document), BC-CALL-NOTES (notes template)

## Win State

When Jamie says "I've got a call with [Name] at [time]", Rich immediately:
1. Pulls all data we have on this person
2. Structures it into a Sandler call plan
3. Identifies what we DON'T know and generates questions to fill gaps
4. Outputs a ready-to-use call prep doc Jamie can skim before the call

## Trigger

- Jamie tells Rich a call is booked → skill runs immediately
- OR: `callBooked` column in H1 gets populated → auto-trigger (future)

## Sandler Selling System (David Sandler)

Seven-stage "submarine" model — complete each stage before moving to the next. Qualification-focused: the buyer convinces the seller to sell, not the other way around.

### Stage 1: Bonding & Rapport
Build psychological safety so they'll be honest about pain, budget, and decision-making.
- What do we have in common? (interests, background, mutual connections)
- What's their communication style? (direct, reflective, analytical, expressive)
- Personal hooks from their LinkedIn content
- What do they care about outside work?

### Stage 2: Up-Front Contract
Set expectations for the conversation — what we'll cover, how long, what happens at the end.
- "I'm going to ask some direct questions to understand your situation. At the end, we'll both decide if it makes sense to work together. Sound good?"
- Removes pressure from both sides
- Pre-planned based on what we know about their situation

### Stage 3: Pain (The Pain Funnel — 3 levels)
The most critical stage. Three levels of pain:

**Level 1 — Surface pain (what they say first):**
- "What's going on?" / "What prompted you to connect?"
- "Tell me more about that"
- "Can you be more specific?"
- "Give me an example"

**Level 2 — Business impact (cost of the problem):**
- "How long has this been going on?"
- "What have you tried to do about it?"
- "Did that work? Why not?"
- "How much do you think that has cost you?" (time, money, opportunities)

**Level 3 — Personal impact (emotional/personal stakes):**
- "How is this affecting you personally?"
- "How do you feel about that?"
- "Have you given up trying to fix this?"

Third-level pain is where buying motivation lives. People buy to fix personal pain, not just business metrics.

### Stage 4: Budget
Qualify early — don't wait until the end.
- Are they willing and able to invest the time, money, and resources?
- "If we found something that worked, what kind of investment would you be comfortable with?"
- "Have you set aside resources to address this?"
- Don't present pricing until pain is established and budget is qualified

### Stage 5: Decision
Who decides, how, and when?
- "Besides yourself, who else would be involved in this decision?"
- "What does your decision-making process look like?"
- "Is this a priority right now? Where does it rank?"
- "Is this the right time?"
- "When would you ideally want to get started?"
- "What would you need to see/know to make a decision?"

### Stage 6: Fulfillment
Present solution ONLY after pain, budget, and decision are qualified.
- Map solution directly to THEIR specific pain points (not generic pitch)
- Reference: BC-OFFER-V1 → `reference/offer-v1.md`
- Deliverables tailored to what they said they need
- Pricing within the budget they indicated
- "Based on what you've told me about [pain], here's how we'd address that..."

### Stage 7: Post-Sell
Prevent buyer's remorse, establish next steps.
- Confirm the decision
- Set clear next steps with dates
- "What could cause you to change your mind?"
- Discuss onboarding / what happens next
- Follow-up plan

## Call Plan Document Structure

### Section 1: RAPPORT PREP (pre-call)
Auto-populated from available data:
- **Their business:** [from H1, RESEARCH tab, PB data, Sales Nav]
- **Their role:** [headline, experience]
- **Shared context:** [mutual connections, groups, interests, locations]
- **Personal hooks:** [from LinkedIn posts — NON-marketing content]
- **Conversation history:** [LinkedIn DM thread summary — what we discussed, what hook they responded to]
- **What brought them here:** [which intro resonated, what they replied, any problems they mentioned]

### Section 2: UP-FRONT CONTRACT DRAFT
Pre-written based on what we know:
- Agenda suggestion
- Time allocation
- Expected outcome framing

### Section 3: PAIN EXPLORATION PREP
Based on signals from their content/messages:
- **Known/suspected pain points:** [from H1 problem tags, LinkedIn posts, DM conversation]
- **Pain level assessment:** Do we have Level 1 only? L2? L3?
- **Questions to deepen pain:**
  - L1 → L2: "You mentioned [X] — how long has that been going on? What have you tried?"
  - L2 → L3: "How is [problem] affecting you personally? Beyond the business impact?"
- **Gap questions:** What pain areas haven't we explored yet?

### Section 4: BUDGET NOTES
- Any signals about budget capacity (company size, funding stage, pricing sensitivity)
- Suggested framing for budget conversation
- Reference: current pricing from BC-OFFER-V1

### Section 5: DECISION PROCESS NOTES
- Who else might be involved? (solo founder = just them; funded startup = board/advisors?)
- Timeline signals from conversation
- Priority ranking clues

### Section 6: FULFILLMENT PREP
- Which parts of the offer map to THEIR specific pain?
- Tailored talking points (not generic)
- Objection prep based on their profile
- Reference: BC-OFFER-V1 for full offer details

## Data Sources (check in order)

1. **H1 sheet** — all columns for this lead's row
2. **RESEARCH tab** — bio, posts, problem indicators, language tags
3. **PB activity data** — full post history
4. **LinkedIn DM history** — conversation thread (requires browser or manual input)
5. **Sales Nav export** — company, location, connections
6. **aiNotes column** — context from intro writing

## Sub-Tasks

| # | Task | Status |
|---|------|--------|
| 1 | Build `skills/pre-call-prep/SKILL.md` with full Sandler process | CAPTURED |
| 2 | Create `reference/call-plan-template.md` | CAPTURED |
| 3 | Wire to H1 `callBooked` column trigger | CAPTURED |
| 4 | Test with mock call | CAPTURED |

## Decision Log

- 2026-02-11: Task created. Jamie specified Sandler selling framework (not SPIN). Seven stages: Bonding, Up-Front Contract, Pain (3 levels), Budget, Decision, Fulfillment, Post-Sell. Must reference offer doc (BC-OFFER-V1).
- 2026-02-11: Corrected from SPIN to Sandler after Jamie flagged the error. Key difference: Sandler qualifies budget and decision-making BEFORE presenting the offer. Pain Funnel has three levels (surface → business impact → personal impact).
