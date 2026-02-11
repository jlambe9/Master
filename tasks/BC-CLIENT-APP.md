# BC-CLIENT-APP — Client-Facing ADHD Coaching App (Clawdbot-Based)

> **Summary:** Productise Clawdbot as the coaching delivery mechanism. Each client gets their own private AI companion via Telegram that delivers their protocol, captures tasks, tracks adherence, and sends consented summaries to Jamie.

**Domain:** boss/product
**Priority:** 🟡 HIGH (builds alongside Founders Program — not before)
**Status:** CAPTURED
**Type:** EXPLORE → EXPLOIT
**Cat:** 🔴 A-S (product differentiator)
**Created:** 2026-02-11

## Why This Exists

ADHD coaching without a delivery system is broken by design. You're telling people with executive function deficits to remember to do things — that's the problem they're paying you to solve. The app IS the coaching, not a separate product.

## Product Vision

Each coaching client gets a private Telegram-based AI companion that:
1. **Delivers their protocol** (morning routine, supplements, habits, exercises)
2. **Captures tasks and blockers** in real-time as they chat
3. **Records processes** as the client does them → validates → can automate
4. **Tags friction points** to identify highest-leverage automation opportunities
5. **Sends consented summaries** to Jamie for coaching prep
6. **Maintains memory** across sessions (unlike a human coach who forgets)

## Competitive Moat

No ADHD coach has this. The typical ADHD coaching experience:
- Weekly call → "how did it go?" → client forgot what happened → generic advice → repeat
- Homework assigned → client forgets → guilt → avoidance

BodyCog experience:
- AI companion pings them daily with their protocol
- They tell the bot what's working/not working in real-time
- Bot captures it all, identifies patterns
- Jamie sees a structured summary before each call
- Call is targeted, specific, data-informed
- Client feels supported between calls (daily Telegram access)

## Architecture

### V1: Founders Program (3-5 clients)

**Each client = separate Clawdbot instance on Jamie's Mac Mini (or VPS)**

Simple, no multi-tenant needed at this scale.

```
~/clients/
  jack-penman/          # Each client = a workspace
    PLAN.md             # Their current focus + tasks
    PROTOCOL.md         # Their personalised protocol
    MEMORY.md           # What the bot remembers about them
    HEARTBEAT.md        # Check-in schedule
    CONSENT.md          # What they've agreed to share
    journal/            # Daily logs
    progress/           # Tracking data
```

**Stack:**
- Telegram bot (one per client, created via BotFather)
- Clawdbot gateway (one per client, different port)
- Shared LLM API keys (Jamie's accounts)
- Coach report cron → sends to Jamie's Telegram

### V2: Multi-Tenant (10+ clients)
- Single server, multiple workspaces
- Shared Clawdbot process with workspace routing
- Client management dashboard
- Automated provisioning

### V3: Standalone App (50+ clients)
- Purpose-built mobile app (or progressive web app)
- Cloud backend replacing filesystem
- Process recording + automation engine
- Proper onboarding flow
- Self-serve sign-up

## Privacy & Consent Layer

### Principle: Client owns their data. Jamie sees ONLY what they consent to.

**During onboarding call, agree on share categories:**

| Category | Example | Default |
|----------|---------|---------|
| Protocol adherence | "Did 5/7 days this week" | ✅ Shared |
| Task completion | "Completed 12/18 tasks" | ✅ Shared |
| Energy/mood scores | "Avg energy: 6.2 → 7.1" | ✅ Shared |
| Themes/patterns | "Mornings strong, afternoons crashing" | ✅ Shared |
| Blockers flagged | "Can't start tasks after lunch" | ✅ Shared |
| Self-ratings | "Week rating: 7/10" | ✅ Shared |
| Private journal | Raw journal entries | ❌ Private |
| Raw conversations | Full chat history | ❌ Private |
| Personal notes | Anything flagged private | ❌ Private |

**Config stored in client workspace:**
```yaml
# CONSENT.md
coach: jamie
share_categories:
  - protocol_adherence
  - task_completion
  - energy_mood
  - themes_patterns
  - blockers
  - self_ratings
private:
  - journal
  - conversations
  - personal_notes
report_frequency: daily  # or pre-session
preview_before_send: true  # client sees summary before it goes to coach
```

### Coach Report Format
```
📊 [Client Name] — Week [N] Summary
Protocol adherence: X/7 days
Missed: [days] ([reason if given])
Energy trend: ↑/↓/→ (avg X.X → Y.Y)
Theme: [AI-identified pattern]
Blocker: "[their words]"
Tasks completed: X/Y
Self-rating: X/10
Flag: [anything unusual — e.g. "3 days no check-in"]
```

## One-Click Client Setup (V1)

### What the client does:
1. Jamie sends them a link during/after onboarding call
2. They click "Start" on their Telegram bot
3. Bot asks 5 onboarding questions:
   - Name + preferred name
   - ADHD diagnosed? Any other ND?
   - Top 3 things they want to work on
   - What time do they wake up / best time for morning ping
   - Consent: review share categories, confirm

### What the setup script does:
```bash
# client-setup.sh [client-name] [telegram-bot-token] [port]
1. Create workspace from template: ~/clients/[name]/
2. Populate template files (PLAN.md, PROTOCOL.md, HEARTBEAT.md, CONSENT.md)
3. Configure gateway (Telegram bot token, port, LLM keys)
4. Set up crons:
   - Morning briefing (client's wake time + 30 min)
   - Evening check-in (21:00)
   - Coach report (day before scheduled call)
5. Configure SOUL.md for client-facing persona
6. Start gateway service
7. Send welcome message to client
```

### Pre-requisites (Jamie does once):
- Create Telegram bot via BotFather (one per client)
- Run setup script with bot token
- Configure their protocol based on onboarding call

### Template workspace files:
- `SOUL.md` — Client-facing persona (supportive, structured, ADHD-aware)
- `PLAN.md` — Their protocol + tasks (populated from onboarding)
- `HEARTBEAT.md` — Check-in schedule
- `CONSENT.md` — Privacy config
- `PROTOCOL.md` — Their personalised metabolic/habit protocol
- `journal/` — Daily logs (auto-populated from check-ins)

## Process Recording & Automation (V2+)

### How it works:
1. Client describes doing a task: "I just did my morning supplements — took magnesium, omega-3, then made coffee"
2. Bot records this as a process draft
3. After 3 consistent repetitions: "I notice you do supplements → coffee every morning. Want me to add this to your morning checklist?"
4. Client confirms → process is now tracked/automated
5. If they miss it, bot pings: "Hey, noticed you haven't done your morning supplements yet"

### Friction tagging:
- Bot tracks where clients struggle most (lowest completion rates)
- Tags tasks by friction level
- Reports to Jamie: "Highest friction: afternoon tasks (32% completion vs 78% morning)"
- Informs coaching: focus on reducing afternoon friction

## Sub-Tasks

| # | Type | Task | Status | Priority |
|---|------|------|--------|----------|
| 1 | EXPLOIT | Create client workspace template files | CAPTURED | P1 — needed for Founders Program |
| 2 | EXPLOIT | Write client-setup.sh script | CAPTURED | P1 |
| 3 | EXPLOIT | Create client-facing SOUL.md persona | CAPTURED | P1 |
| 4 | EXPLOIT | Build coach report cron + format | CAPTURED | P1 |
| 5 | EXPLOIT | Create onboarding flow (Telegram) | CAPTURED | P1 |
| 6 | EXPLORE | Process recording prototype | CAPTURED | P2 — after first clients |
| 7 | EXPLORE | Friction tagging system | CAPTURED | P2 |
| 8 | EXPLORE | Multi-tenant architecture | CAPTURED | P3 — when >5 clients |
| 9 | EXPLORE | Standalone app feasibility | CAPTURED | P4 — when >20 clients |

## Dependencies

- **BC-OFFER-V1** — defines what the Founders Program includes (this is a deliverable within it)
- **BC-PRECALL-PREP** — coach report feeds into pre-call prep
- **Founders Program clients** — need actual clients to build for

## Key Decisions Needed

1. Client-facing persona — how should the bot sound? (Not Rich — something purpose-built)
2. Protocol format — how is the metabolic protocol structured in files?
3. Pricing for ongoing bot access post-coaching (subscription model?)
4. Data retention — how long do we keep client data?

## Decision Log

- 2026-02-11: Product vision captured. Key insight: the app IS the coaching delivery mechanism, not a separate product. ADHD clients need a single source of truth with zero-activation-energy access. Telegram is the MVP app — zero download, already on their phone.
- 2026-02-11: Privacy architecture defined. Client owns data, Jamie sees only consented summaries. Preview-before-send option.
- 2026-02-11: One-click setup concept — script creates workspace from template, configures gateway, sets up crons. Client just clicks "Start" on Telegram.
