# PROCESSES.md — Process Registry

*To define a new process: use `templates/process-map.md`. Then add it here and link from the relevant boss/ file.*
*To score a process as a task: use `task-system/layer0-scoring.md` → log to `task-system/task-log.md`.*

## ✅ Defined & Active

| Process | Where Documented | Last Verified | Boss Domain |
|---------|-----------------|---------------|-------------|
| ClawdBot boot sequence | ClawdBot: BOOT.md | 2026-02-09 | infrastructure |
| ClawdBot heartbeat | ClawdBot: HEARTBEAT.md | 2026-02-09 | infrastructure |
| Expandi monitoring | ClawdBot: skills/expandi/RUNBOOK.md | 2026-02-09 | lead-gen |
| Ad creative production | Claude web: bodycog-ad-wizard skill | 2026-02-09 | lead-gen |

## 🟡 Partially Defined

| Process | What Exists | What's Missing | Boss Domain |
|---------|-------------|----------------|-------------|
| LinkedIn intro writing | Rules in ClawdBot | End-to-end flow, quality verification | lead-gen |
| LinkedIn FU sequence (FU1–breakup) | Timing + specs in playbooks/ | Automation, A/B testing | lead-gen |
| Lead extraction | PhantomBuster scripts | Automation, error handling | lead-gen |
| Daily review | Template exists | ClawdBot automation, cron job | infrastructure |
| Thesis research pipeline | MCP tools, Bradford Hill grading | Documented workflow | research |

## ❌ Not Yet Defined

| Process | Priority | Boss Domain | Notes |
|---------|----------|-------------|-------|
| Client onboarding | CRITICAL | product | Must exist before first paying client |
| Sales call workflow | HIGH | sales | Script, booking, follow-up |
| 14-day challenge delivery | HIGH | lead-nurture | Primary conversion mechanism |
| Follow-up sequences | HIGH | lead-nurture | Defined in `playbooks/linkedin-personalisation.md` — needs automation |
| Content publishing (organic) | MEDIUM | lead-gen | Calendar, creation, scheduling |
| Weekly review compilation | MEDIUM | infrastructure | ClawdBot automated |
| HMRC quarterly filing | MEDIUM | finance | bodycog-admin |
| GDPR/data handling | HIGH | legal-hr | Before first client |
| Outcome measurement | HIGH | product | Assessment protocols designed but not operationalised |
| Morning mobile task queue | LOW | infrastructure | Tasks for cardio window |
| Cross-tool context sync | LOW | ai/infrastructure | Partially solved by /master |
