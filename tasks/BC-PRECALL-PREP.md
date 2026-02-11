# BC-PRECALL-PREP — Sales Call Prep Skill

> **Summary:** Create a skill that auto-generates a SPIN-structured call plan when a sales call is booked. Pulls all available data (LinkedIn convo, H1 data, profile) and identifies information gaps + questions to fill them.

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
2. Structures it into a SPIN call plan
3. Identifies what we DON'T know and generates questions to fill gaps
4. Outputs a ready-to-use call prep doc Jamie can skim before the call

## Trigger

- Jamie tells Rich a call is booked → skill runs immediately
- OR: `callBooked` column in H1 gets populated → auto-trigger (future)

## SPIN Selling Framework (Neil Rackham)

### S — Situation (context gathering)
Understanding their current world before probing for problems.
- What's their business? Industry? Size? Stage?
- What's their role? How long in it?
- What's their daily like? (from LinkedIn content/convo)
- Personal context: interests, values, shared connections
- Current tools/approaches they use for performance/health/focus

### P — Problem (pain identification)
What specific problems are they experiencing?
- What's not working? What frustrates them?
- What symptoms are they noticing? (energy, focus, consistency, burnout)
- How long has this been going on?
- What triggered it? (growth, new role, life change)

### I — Implication (cost of inaction)
What's the IMPACT of these problems?
- How is it affecting their business/revenue/team?
- What opportunities are they missing?
- What's the personal cost? (health, relationships, fulfilment)
- What happens if nothing changes in 6-12 months?
- What have they tried before? Why didn't it work?

### N — Need-Payoff (solution framing)
Getting THEM to articulate what they want and why it matters.
- What would "fixed" look like for them?
- If they had consistent energy/focus, what would change?
- What would solving this be worth to them?
- Do they actually want to fix this? Is it a priority NOW?
- Where does it rank vs other priorities?
- Is this the right time?
- What would they need from a solution?
- When would they want to get started?
- What structure/format works best for them?

## Call Plan Document Structure

### Section 1: RAPPORT (pre-call prep)
Auto-populated from available data:
- **Their business:** [from H1, RESEARCH tab, PB data, LinkedIn]
- **Their role:** [headline, experience]
- **Shared context:** [mutual connections, groups, interests]
- **Personal hooks:** [from LinkedIn posts, shared interests, locations]
- **Conversation history:** [what we discussed in LinkedIn DMs]
- **What brought them here:** [which intro/hook resonated, what they replied]

### Section 2: SITUATION QUESTIONS (what we need to learn)
Pre-generated based on gaps in our data:
- ✅ Known: [list what we already know]
- ❓ Unknown: [list what we need to find out]
- 📝 Questions to ask: [specific questions to fill gaps naturally]

### Section 3: PROBLEM EXPLORATION
Based on signals from their content/messages:
- **Suspected problems:** [from problem tags in H1, LinkedIn posts]
- **Questions to confirm/explore:**
  - "You mentioned [X] in your post — is that something you're still dealing with?"
  - "How does [suspected problem] show up day-to-day for you?"
  - "How long has that been going on?"

### Section 4: IMPLICATION QUESTIONS
Pre-written based on suspected problems:
- "What's the impact of [problem] on [their business]?"
- "What have you tried before to address this?"
- "Why do you think that didn't work?"
- "If nothing changes in the next 6 months, what happens?"

### Section 5: NEED-PAYOFF QUESTIONS
- "If you could fix [problem], what would that change for you?"
- "Is this something you're actively looking to solve right now?"
- "Where does this sit on your priority list?"
- "What would an ideal solution look like for you?"
- "When would you want to get started?"

### Section 6: PRESENT OFFER
Reference: `~/Master/tasks/BC-OFFER-V1.md` → `reference/offer-v1.md` (when written)
- Mechanism overview (tailored to THEIR specific problems)
- Deliverables
- Pricing
- Next step / commitment question

### Section 7: OBJECTION NOTES
Pre-loaded from offer doc, tailored to this lead's likely objections based on profile.

## Data Sources (check in order)

1. **H1 sheet** — all columns for this lead's row
2. **RESEARCH tab** — bio, posts, problem indicators, language tags
3. **PB activity data** — full post history
4. **LinkedIn DM history** — conversation thread (requires browser)
5. **Sales Nav export** — company, location, connections
6. **aiNotes column** — any context from intro writing

## Sub-Tasks

| # | Task | Status |
|---|------|--------|
| 1 | Build `skills/pre-call-prep/SKILL.md` with full process | CAPTURED |
| 2 | Create call plan template at `reference/call-plan-template.md` | CAPTURED |
| 3 | Wire to H1 `callBooked` column trigger | CAPTURED |
| 4 | Test with mock call | CAPTURED |

## Decision Log

- 2026-02-11: Task created. Jamie described SPIN-based pre-call prep that auto-pulls data and generates question plan. Must reference offer doc (BC-OFFER-V1).
