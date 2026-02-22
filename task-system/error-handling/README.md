# Error Handling — Centralised Playbooks

The system's institutional memory for errors. Every error either has a known resolution here or generates a new entry after resolution.

## Directory Layout

| File | Category | What It Covers |
|------|----------|---------------|
| `cron-errors.md` | 🔧 Cron | Cron failures: didn't fire, wrong model, no output, timeout, delivery failure |
| `tool-errors.md` | 🔨 Tool | External tool failures: Expandi, H1/Sheets, browser, PhantomBuster, APIs |
| `infra-errors.md` | 🏗️ Infrastructure | OpenClaw/gateway failures: config breaks, model fallback, auth, restart, compaction |
| `domain-leadgen.md` | 🏢 Domain: Lead Gen | Lead gen pipeline failures: bad leads, missing data, volume shortfalls |
| *(future domains)* | 🏢 Domain: [name] | Add one file per business domain as domains are added |

## Error Categories

**🔧 Cron errors** — the scheduled job itself failed. It didn't fire, fired on wrong model, produced no output, timed out, or delivered to wrong target.

**🔨 Tool errors** — an external tool the system depends on failed. Expandi API, Google Sheets, browser automation, PhantomBuster, search APIs.

**🏗️ Infrastructure errors** — the OpenClaw platform itself failed. Gateway config, model routing, authentication, process crashes, compaction issues.

**🏢 Domain errors** — errors specific to a business domain's logic. Lead is a competitor, intro data missing, pipeline stage wrong. These are business logic failures, not tool failures.

**📋 Task-specific errors** — errors unique to one task's process. These live IN the task file's "Error Handling / Known Edge Cases" section, NOT here. Rule: if the error could happen to any task using the same tool → put it in the tool playbook here. If it's specific to this task's unique process → put it in the task file.

## Entry Template

Every playbook entry follows this format:

**Error: [descriptive name]**
- Pattern: What you see (symptoms, error messages, observable behaviour)
- Likely cause: Why this happens
- Resolution: Step-by-step fix
- Prevention: What stops it recurring (config change, rule addition, monitoring)
- Severity: 🔴 Blocks system / 🟡 Degrades system / 🟢 Cosmetic
- First seen: [date] — [context of when we first hit this]

## How Agents Find Resolutions

1. AGENTS.md error handling protocol tells you to come here
2. Read this README to identify which playbook covers your error category
3. Open the correct playbook and search for matching error pattern
4. If found → follow resolution steps
5. If not found → check ALL playbooks (error might be miscategorised)
6. If still not found → it's a new error. Log it, fix it, create a playbook entry

## How to Add a New Error Type

1. Determine category (cron / tool / infra / domain / task-specific)
2. If task-specific → add to the task file's Error Handling section, not here
3. Otherwise → open the correct playbook file
4. Copy the entry template above
5. Fill all fields — especially "First seen" so we know this is from real experience
6. If it's a new domain → create `domain-[name].md` following the same format

## How This Integrates with Crons

Every cron prompt includes error handling instructions:
- On error → check the relevant playbook in `task-system/error-handling/`
- If known resolution → follow it
- If unknown → log to `memory/error-log/YYYY-MM-DD.md` + alert Jamie

## How This Integrates with the Decision Log

When an error leads to a system change (config change, new rule, process modification):
1. Log the error here (playbook entry)
2. Log the decision in the relevant task/goal Decision Log
3. Cross-reference: playbook entry links to decision, decision links to playbook entry
