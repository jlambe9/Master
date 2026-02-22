# Cron Error Playbook

Known cron error patterns and resolutions. Add new entries as errors are encountered.

---

**Error: Cron fires on wrong model (expensive model burns credits)**
- Pattern: Credit usage spikes. Cron output quality is fine but cost is excessive. `cron list` shows cron using Opus or Sonnet where Flash is specified.
- Likely cause: Cron was created or updated without specifying model. OpenClaw defaults to the primary model in config (currently Gemini Flash, but previously was Opus).
- Resolution: (1) `cron list` to identify all cron model assignments. (2) Update any cron using wrong tier via `cron update`. (3) Verify against cron registry — every cron must match its registered model tier.
- Prevention: AGENTS.md Model Tier System rule. No cron ever runs on Opus. Every cron definition specifies model tier explicitly.
- Severity: 🟡 Degrades system (cost blowout, not functional failure)
- First seen: 2026-02-18 — all crons running on Opus, burned through daily credits by midday

---

**Error: All crons broken after gateway config change**
- Pattern: Multiple crons fail simultaneously. No outputs produced. System health (if running) reports all crons missed. Usually follows a config change or model switch.
- Likely cause: Config change altered the default model or fallback chain to a model that doesn't work (wrong API key, model not available, model can't handle tool calls).
- Resolution: (1) `gateway config.get` — check current model config. (2) Verify primary model and ALL fallbacks are valid. (3) Test with a simple cron or sub-agent spawn. (4) If model is broken, `gateway config.patch` to restore working model. (5) Restart gateway. (6) Verify crons resume.
- Prevention: Never change the default model without testing a cron on the new model first. Keep Sonnet in the fallback chain as a reliable backup. Document working config state before changes.
- Severity: 🔴 Blocks system (nothing works)
- First seen: 2026-02-19 — switched to Gemini Flash Lite as default, broke all crons for 2 days, no remote recovery method

---

**Error: Cron fires but produces no output**
- Pattern: Cron appears in `cron list` with correct schedule. Last run shows no error. But no output file at expected location (`memory/cron-outputs/[name]/YYYY-MM-DD.md`).
- Likely cause: (a) Model couldn't handle the prompt (too long, too complex for Flash). (b) Input files the cron reads don't exist. (c) Cron prompt doesn't include output writing instruction. (d) Session timed out silently.
- Resolution: (1) Check cron prompt — does it explicitly say where to write output? (2) Check input files exist at expected locations. (3) Check model tier — is the task too complex for the assigned model? (4) Fire cron manually via `cron run` and watch for errors. (5) If model issue, consider upgrading to next tier or simplifying prompt.
- Prevention: Cron template requires explicit output location. System health cron checks output directories for freshness.
- Severity: 🟡 Degrades system (downstream processes have no data)
- First seen: Multiple instances — common when prompts are too complex for Flash

---

**Error: Cron delivery target wrong (messages go nowhere)**
- Pattern: Cron fires, output may be produced, but Jamie never receives the alert/message. No error visible.
- Likely cause: Delivery target in cron definition is wrong. Previously had names instead of chat IDs (e.g. "Jamie Lambe" instead of `telegram:1140538997`).
- Resolution: (1) `cron list` — check delivery targets on all crons. (2) Correct any that don't use the format `telegram:1140538997`. (3) Test with a manual `cron run`.
- Prevention: All cron definitions use `telegram:1140538997` as delivery target, never names. Validated during cron creation.
- Severity: 🟡 Degrades system (crons work but nobody sees the output)
- First seen: 2026-02-20 — multiple crons delivering to wrong target after config migration

---

**Error: Cron timeout — task too large for model**
- Pattern: Cron starts but never completes. No output produced. May show as "running" in session list.
- Likely cause: Prompt requires reading too many files or producing too much output for the model's context window or timeout setting.
- Resolution: (1) Check cron timeout setting — increase if needed. (2) Check prompt complexity — can checks be simplified or split? (3) If daily integrity cron, consider whether all 6 checks are too much for one Flash agent. (4) If splitting needed, create two crons with clear scope division.
- Prevention: Cron template includes timeout constraint. Complex crons tested manually before scheduling.
- Severity: 🟡 Degrades system (checks don't run)
- First seen: Anticipated — not yet hit but likely as daily integrity cron grows
