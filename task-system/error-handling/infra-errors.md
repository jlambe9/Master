# Infrastructure Error Playbook

Known OpenClaw/gateway infrastructure error patterns and resolutions. THE critical playbook — these errors take down the entire system.

---

**Error: Gateway config change breaks model routing**
- Pattern: After a config change (model switch, env update, config.patch), all or most agent sessions fail. Crons stop producing output. Sub-agents fail to spawn. System appears dead.
- Likely cause: Config change set the default model to one that's unavailable, misconfigured, or can't handle the required tools/context.
- Resolution:
  1. `gateway config.get` — read current config, identify what changed
  2. Check `agents.defaults.model.primary` — is this model valid and available?
  3. Check `agents.defaults.model.fallbacks` — is the fallback chain intact?
  4. Test: spawn a simple sub-agent (`sessions_spawn` with a trivial task) to verify the model works
  5. If model is broken: `gateway config.patch` to set primary back to a known-working model (Gemini Flash: `google/gemini-3-flash-preview`)
  6. Gateway restarts automatically after config.patch
  7. Verify: `cron list` — are crons scheduled? Fire one manually to test
  8. If remote (via Telegram): you CAN run `gateway config.patch` from the main session — this is the recovery path
- Prevention: Before any config change: (a) document current working state, (b) test new model with a sub-agent BEFORE making it the default, (c) always keep Sonnet in the fallback chain as reliable backup
- Severity: 🔴 Blocks system (nothing works)
- First seen: 2026-02-19 — switched to Gemini Flash Lite, broke everything for 2 days

---

**Error: Model fallback cascade exhausted**
- Pattern: Primary model fails. Fallback 1 fails. Fallback 2 fails. All fallbacks fail. Agent session returns error.
- Likely cause: (a) API keys expired/invalid for multiple providers. (b) Rate limiting across providers. (c) All configured models are from the same provider which is down.
- Resolution:
  1. Check which provider is failing: look at error messages for API errors
  2. If Anthropic down: verify Gemini and xAI still work
  3. If all providers down: this is rare — wait and retry
  4. If API key issue: `gateway config.get` → check env section for valid keys
  5. Current fallback chain: Flash → Grok → Flash Lite → Gemini Flash → Sonnet
  6. Ensure fallback chain spans at least 2 providers
- Prevention: Fallback chain must include models from at least 2 different providers. Never have all fallbacks from one provider.
- Severity: 🔴 Blocks system
- First seen: Partial — Anthropic auth failures intermittent since 2026-02-20

---

**Error: Anthropic auth intermittent failures on sub-agents**
- Pattern: Sub-agent spawns fail with auth errors. Main session (Opus) works fine. Sub-agents on Sonnet or other Anthropic models fail intermittently — sometimes work, sometimes don't.
- Likely cause: Rate limiting or token validation differences between main session (claude-max subscription) and API sub-agent sessions. Possibly different auth profiles being used.
- Resolution:
  1. Check auth profiles: `gateway config.get` → `auth.profiles` — are there multiple Anthropic profiles?
  2. If intermittent: retry with same model (often works on second attempt)
  3. If persistent: switch sub-agent to a different provider model (e.g. Gemini Flash)
  4. Log frequency — if it's happening >20% of the time, something is wrong with the auth config
- Prevention: Monitor sub-agent failure rate. If Anthropic auth is unreliable for sub-agents, default sub-agents to Gemini models.
- Severity: 🟡 Degrades system (sub-agents fail, work doesn't get done, but main session still works)
- First seen: 2026-02-20 — 4+ failures on sub-agent spawns

---

**Error: OpenClaw process dies / needs restart**
- Pattern: Telegram messages go unanswered. Crons don't fire. Gateway doesn't respond.
- Likely cause: (a) Process crashed. (b) Mac mini went to sleep. (c) Node.js error killed the process.
- Resolution:
  1. If Jamie has terminal access: `openclaw gateway status` → check if running
  2. If not running: `openclaw gateway start`
  3. If running but unresponsive: `openclaw gateway restart`
  4. Verify: send a test message via Telegram, check for response
  5. Check crons resumed: `cron list` — verify schedules are active
- Prevention: Mac mini sleep settings should prevent sleep during operating hours. Consider a launchd service to auto-restart.
- Severity: 🔴 Blocks system (everything dead)
- First seen: Multiple — happens occasionally, usually after Mac updates or sleep

---

**Error: Persona lost after compaction**
- Pattern: Agent behaviour quality drops. Systems architecture work done without Atlas principles. Agent doesn't follow specialist protocols. Usually only noticed when Jamie spots the quality drop.
- Likely cause: Context compaction summarised conversation content but didn't preserve which persona was loaded. Agent resumes as base Rich without specialist knowledge.
- Resolution:
  1. Check `memory/YYYY-MM-DD.md` Active State section — which persona was loaded?
  2. Reload the persona: `read ~/Master/personas/[persona].md`
  3. Continue work with persona loaded
- Prevention: memoryFlush prompt now requires persona tracking (fixed 2026-02-22). AGENTS.md Persona Loading section tells agents to check memory after compaction. Memory Active State section records loaded persona.
- Severity: 🟡 Degrades system (work quality drops, may need to redo)
- First seen: 2026-02-22 — Atlas persona not loaded after compaction, systems work done without specialist principles

---

**Error: Telegram delivery failure (wrong chat ID)**
- Pattern: Messages/alerts sent by crons or sub-agents never arrive. No error visible on the agent side.
- Likely cause: Delivery target uses a name ("Jamie Lambe") instead of chat ID, or wrong chat ID format.
- Resolution:
  1. Verify target format: must be `telegram:1140538997`
  2. Check all cron delivery targets: `cron list`
  3. Check message tool calls: must use `target` field (not `to`) with correct ID
  4. Test: send a test message via `message send` to `telegram:1140538997`
- Prevention: All delivery targets hardcoded to `telegram:1140538997`. Never use names. Validated during cron creation.
- Severity: 🟡 Degrades system (work happens but Jamie doesn't know about it)
- First seen: 2026-02-20 — multiple crons delivering to wrong target

---

**Error: Credit/cost blowout from wrong model assignment**
- Pattern: API credits consumed much faster than expected. Daily budget hit by midday. Usage dashboard shows high-cost model calls where cheap ones expected.
- Likely cause: Crons or sub-agents running on Opus or other expensive models instead of Flash/Sonnet.
- Resolution:
  1. `cron list` — check model assignment on every cron
  2. Check recent sub-agent spawns — were model overrides specified?
  3. Update any misassigned crons to correct tier
  4. Check AGENTS.md Model Tier System — is it being followed?
- Prevention: Model Tier System in AGENTS.md. No cron ever runs on Opus. Sub-agent spawns must specify model. System health cron could audit model assignments.
- Severity: 🟡 Degrades system (runs out of credits, then becomes 🔴)
- First seen: 2026-02-18 — all crons on Opus, credits exhausted
