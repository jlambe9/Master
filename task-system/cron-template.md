# Cron Definition Template

> Copy this template when creating a new cron. Fill every field. Register in v1.3-cron-registry.md.

## Header

| Field | Value |
|-------|-------|
| **Name** | CRON-[NAME] |
| **One-liner** | Plain English: what this cron does and why it matters |
| **Scope** | 🔧 System (task manager infrastructure) / 🏢 Domain ([domain name]) |
| **Model Tier** | Validation (Flash) / Judgment (Sonnet) — never Opus |
| **Schedule** | Cron expression + human-readable (e.g. `0 7 * * *` — daily 07:00 GMT) |
| **OpenClaw Cron ID** | [filled after deployment] |

## Trigger

What kicks this cron off: schedule only, or does it also depend on another cron's output existing?

| Field | Value |
|-------|-------|
| **Trigger type** | Schedule / Schedule + upstream dependency |
| **Upstream dependency** | None / CRON-[NAME] output must exist at [path] |

## Inputs

What the cron reads before doing its work.

| Input | Location | Required? |
|-------|----------|-----------|
| [e.g. Goal files] | ~/Master/goals/*.md | Yes |
| [e.g. Previous cron output] | memory/cron-outputs/[name]/YYYY-MM-DD.md | Yes |

## Checks

What the cron validates or computes. Each check is independent — failure on one does not block others.

| # | Check | Pass condition | Fail action |
|---|-------|---------------|-------------|
| 1 | [e.g. All task files have Goal field] | Every .md in tasks/ has Goal: line | Log violation, include in report |

## Outputs

What the cron produces and where it writes.

| Output | Location | Format |
|--------|----------|--------|
| Cron report | memory/cron-outputs/[name]/YYYY-MM-DD.md | Structured markdown with sections per check |
| Alert (if problems) | Jamie via Telegram | Plain text summary |

## Error Handling

What happens when the cron itself fails.

| Error type | Resolution | Playbook ref |
|------------|------------|-------------|
| Model unavailable | Fallback to next tier (Flash→Flash Lite) | error-handling/cron-errors.md |
| Input file missing | Log as MISSING, continue other checks | error-handling/cron-errors.md |
| Timeout | Log, alert Jamie, retry next scheduled run | error-handling/cron-errors.md |

## Constraints

- Sequential execution within this cron (check 1 completes before check 2 starts)
- Must complete within [X] minutes or timeout
- Must not modify source files (read-only) unless explicitly specified in Fail action

## Tools Needed

| Tool | Purpose |
|------|---------|
| [e.g. Read] | Read task/goal files |
| [e.g. exec] | Run validation scripts |

## BPMN Notation

Trigger → Activities → Gateways → Outputs → Error Boundaries

```
[Start: Schedule fires]
  → [Activity: Read inputs]
  → [Activity: Run check 1]
    → [Gateway: Pass?]
      → Yes: [Record pass]
      → No: [Log violation, continue]
  → [Activity: Run check 2]
    → [Gateway: Pass?]
      → Yes: [Record pass]
      → No: [Log violation, continue]
  → [Activity: Write output report]
  → [Gateway: Any failures?]
    → Yes: [Send alert to Jamie]
    → No: [Silent]
  → [End]

[Error Boundary: Model unavailable] → [Fallback model] → [Retry]
[Error Boundary: Timeout] → [Log + alert] → [End]
```

## Validation

How to verify this cron is working correctly after deployment:
1. Fire manually via `cron run`
2. Check output file exists at expected location
3. Check output contains all expected sections
4. If upstream dependency exists, verify it reads the correct file
5. Verify alert fires when a check deliberately fails (test with a malformed file)

---

*After creating: register in v1.3-cron-registry.md under the correct scope section. Link the OpenClaw cron ID.*
