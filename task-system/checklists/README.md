# Operational Checklists — Architecture

*Checklists verify that infrastructure/tools/access are operational at each level.*
*Used by: Atlas dependency tracing, CLAWD-004 daily scan, CLAWD-005 pre-flight, evening planning.*

## Checklist Hierarchy

```
GLOBAL (clawd/ops)
  └── infra health, API keys, gateway, browser, repos
  
DOMAIN (boss/lead-gen, boss/sales, etc)
  └── domain-level prereqs: "is this whole area functional?"
  
SUBDOMAIN (boss/lead-gen/expandi, boss/lead-gen/content, etc)
  └── specific system/tool chain for a subdomain
  
PROCESS (specific task/cron)
  └── "does this specific process have everything it needs to run?"
```

## When Each Level Fires

| Level | When | Example |
|-------|------|---------|
| Global | Daily pre-flight (05:00) via CLAWD-005 | "Are all APIs accessible?" |
| Domain | Evening planning scan (21:00) | "Is lead-gen operational?" |
| Subdomain | When Atlas traces to root of a chain | "Is the Expandi pipeline loaded?" |
| Process | Before a specific cron/task fires | "Does write-intro have browser access?" |

## Checklist Files

| Level | File | Covers |
|-------|------|--------|
| Global | `checklists/global-infra.md` | All APIs, gateway, browser, repos |
| boss/lead-gen | In `task-field-guide.md` domain section | Domain-level prereqs |
| boss/lead-gen/expandi | `checklists/boss-lead-gen-expandi.md` | Full Expandi upstream pipeline |
| boss/sales | In `task-field-guide.md` domain section | Sales prereqs |
| boss/product | In `task-field-guide.md` domain section | Product prereqs |
| clawd/ops | `checklists/global-infra.md` | System health |

## How Atlas Uses Checklists

1. Tracing dependencies → hits root of a chain → check DOMAIN checklist
2. Domain checklist fails → drill into SUBDOMAIN checklist for specifics
3. Subdomain checklist fails → identify specific PROCESS that needs fixing
4. Report: "Root blocker: [checklist item] at [level] is failing. Fix: [action]"

## Adding New Checklists

When a new domain/subdomain/process is created:
1. Add domain-level items to `task-field-guide.md`
2. If complex enough, create `checklists/[domain]-[subdomain].md`
3. Link from the relevant task file's Domain Checklist field
