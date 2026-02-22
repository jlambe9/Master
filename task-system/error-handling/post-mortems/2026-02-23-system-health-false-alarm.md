# Post-Mortem: System Health False Alarm
**Date:** 2026-02-23
**Incident:** "System Health (3x daily)" cron produced a false diagnosis of "critical failure" and recommended manually restarting the OpenClaw gateway.
**Impact:** No functional impact (gateway was fine, user was actively chatting). Trust impact: false alarms erode confidence in the monitoring system.
**Status:** Resolved — cron-errors.md updated with entry #6; prompt fix required (see Recommendations).

---

## What Happened

The System Health cron fired for the first time approximately 30 minutes after the Phase 4 cron batch was deployed. It checked `lastRunAtMs` on each cron, found most returned null/empty (because they hadn't reached their first scheduled window yet), interpreted the absence of data as evidence of failure, and escalated to "critical" — recommending a manual gateway restart. The gateway was functioning normally throughout.

---

## Root Cause Analysis

### 1. Why did the agent interpret "no data" as "failure"?

**The missing context:** The prompt instructed the agent to check `lastRunAtMs` for each cron but provided no logic to distinguish between:
- A cron that *used to fire* and has *stopped*
- A cron that *has never fired* because it hasn't reached its first scheduled window

The prompt contained no instruction to cross-reference `createdAtMs` or any equivalent "age" signal. There was no defined grace period for newly deployed crons.

**What the prompt likely said (reconstructed intent):** Something like *"check lastRunAtMs for each cron and flag any that have missed their expected window."*

**What was missing:**
- A first-run grace period rule: *"If a cron has no lastRunAtMs AND its createdAtMs is < [1 × its schedule interval], it is NEW — do not flag it."*
- An explicit definition of what constitutes a "missed window": a cron misses its window only if `now - lastRunAtMs > (expectedInterval × toleranceFactor)`, **and** `lastRunAtMs` is not null.
- Null/missing `lastRunAtMs` should map to status: **"never fired — not yet due"**, not **"failed."**

**In plain terms:** The agent had no vocabulary for "new and waiting." It only knew "fired" or "failed." The prompt needed to teach it a third state.

---

### 2. Did cron-errors.md help? What should it contain?

**At the time of the incident:** Entry #6 (*"System health cron false-alarms on newly deployed crons"*) was **not present** — it was added *after* this incident as a direct result of it. The five entries that existed covered: wrong model, config-change mass failure, silent no-output, wrong delivery target, and timeout. None of them addressed the "new cron, no history" scenario.

**Did any existing entry help?** No. The closest is the "All crons broken after gateway config change" entry, which describes mass failure — but that entry's resolution path leads toward gateway restart, which is precisely the wrong action here. If the agent had consulted it, it might have reinforced the wrong recommendation.

**What the file SHOULD contain (and now does, as entry #6):**
- The null-`lastRunAtMs` pattern and its correct interpretation
- The `createdAtMs` check as the first diagnostic step
- An explicit statement: *"Never recommend gateway restart without evidence of actual failure (multiple previously-working crons failing simultaneously)"*
- A severity rating that flags this as a trust issue, not a functional failure

**Broader gap:** The file had no entry covering *false positives* at all. Every entry described real failures. The playbook implicitly assumed every alert is a real error. It needs entries for known false-alarm patterns — situations where the *system is fine* but the *monitoring is wrong*.

---

### 3. What validation steps should precede any recommendation?

The agent recommended a gateway restart without verifying whether the gateway was actually broken. The minimum validation chain before escalating any recommendation:

**Before "restart the gateway":**
1. **Prove the gateway is unresponsive.** If you just ran `cron list` and got results, the gateway is alive. A responsive gateway cannot be the root cause.
2. **Isolate the failure to a single cron vs. all crons.** If only some crons show no `lastRunAtMs`, the failure is not gateway-wide.
3. **Check `createdAtMs`** on each flagged cron. If `createdAtMs` < 24h ago (or < 1 scheduled interval), the cron is new — not broken.
4. **Check for a recent deployment event.** Multiple crons deployed simultaneously with no fire history is a strong signal of "just deployed," not "broken."
5. **Attempt a manual `cron run` on one flagged cron.** If it executes successfully, the cron is healthy.
6. **Check the gateway process directly** (`openclaw gateway status`) before recommending restart.

**The general principle:** A recommendation is only valid if the agent has *ruled out the simpler explanation*. The simpler explanation here was "the crons are new." That check takes one step and costs nothing.

**Validation hierarchy (cheapest to most disruptive):**
1. Does my own data contradict the failure hypothesis? (Self-check — free)
2. Is there a contextual explanation? (Age check — free)
3. Is the supposed-broken component actually responding? (Functional test — cheap)
4. Does a manual re-run succeed? (Execution test — medium cost)
5. Only then: recommend intervention.

---

### 4. Self-healing: what the agent can and cannot do

**COULD do (safe, reversible, low-blast-radius):**
- Retry a failed cron manually via `cron run` (non-destructive, good signal)
- Check and report the gateway status without acting on it
- Write a diagnostic summary to a known file path for human review
- Annotate the flagged cron with a note in the daily cron output log
- Cross-reference `createdAtMs` to auto-downgrade a "failure" to "new/waiting"
- Check output directories for freshness and report staleness without recommending action
- Increase its own confidence threshold before escalating — i.e., require 2+ consecutive missed windows before alerting

**SHOULD NEVER do:**
- Restart the gateway autonomously — this terminates all active sessions, including the user's live chat
- Delete or disable a cron it thinks is broken — the cron may be fine
- Modify cron schedules or prompts without human approval
- Send a "critical" alert on a single data point (null `lastRunAtMs`) without corroborating evidence
- Take any action that is irreversible or session-disrupting without explicit human instruction
- Escalate to "critical" based on absence of evidence alone — absence of data ≠ evidence of failure

**The self-healing boundary:** Heal = gather information, retry non-destructive operations, downgrade severity based on context. Do not heal = terminate processes, change configuration, or act on behalf of the user's infrastructure without proof of a real problem.

---

### 5. The precise logical distinction for alert criteria

**What the prompt said (reconstructed):** *"Alert Jamie if a critical cron missed its window."*

**What the agent did:** Alerted for crons that had *never fired* — treating null `lastRunAtMs` as equivalent to "missed window."

**Why this is wrong:** A cron cannot miss a window it has not yet reached. "Missed window" is a statement about a *deviation from an established pattern*. It requires a baseline — at least one successful prior fire — to be meaningful.

**The precise logical distinction the prompt needs to enforce:**

```
MISSED WINDOW (alert-worthy) =
  lastRunAtMs IS NOT NULL
  AND (now - lastRunAtMs) > (expectedInterval × toleranceFactor)

NEW / NEVER FIRED (do not alert) =
  lastRunAtMs IS NULL
  AND createdAtMs > (now - expectedInterval)
```

In natural language, the prompt should read:

> *"A cron has missed its window if and only if: (a) it has fired at least once before (lastRunAtMs is not null), and (b) the time since its last run exceeds its expected interval by more than [tolerance]. A cron with no run history that was created less than [1 interval] ago is NEW — do not flag it. A cron with no run history that was created more than [2 intervals] ago MAY be stuck and can be flagged as a low-priority warning, not critical."*

**The three states the prompt must define:**

| State | Condition | Action |
|---|---|---|
| ✅ Healthy | `lastRunAtMs` recent, within tolerance | No action |
| 🆕 New | `lastRunAtMs` null, `createdAtMs` < 1 interval | Log only, no alert |
| 🔴 Missed | `lastRunAtMs` not null, gap > interval × tolerance | Alert Jamie |
| ⚠️ Stale-new | `lastRunAtMs` null, `createdAtMs` > 2 intervals | Low-priority flag only |

Without these states defined in the prompt, the agent collapses all non-healthy states into "failure." The prompt must provide the vocabulary.

---

## Recommendations

### Immediate (prompt fix required)

1. **Add first-run grace period logic to the System Health cron prompt:**
   > *"Before flagging a cron as missed: check createdAtMs. If the cron is newer than its expected interval, it is NEW — not failed. Do not alert."*

2. **Add explicit null-handling rule:**
   > *"lastRunAtMs = null means the cron has never fired. This is only a problem if createdAtMs was more than [2 × interval] ago."*

3. **Add pre-recommendation validation gate:**
   > *"Before recommending any gateway action: verify the gateway is unresponsive (if you just listed crons successfully, it is NOT unresponsive)."*

4. **Replace "alert if critical cron missed its window" with the three-state logic above.**

### Medium-term (playbook)

5. **cron-errors.md** now contains entry #6 covering this pattern. Verify the resolution steps are followed in the updated prompt.

6. **Add a "false alarm" section to cron-errors.md** — a dedicated category for known monitoring false positives, separate from real failure patterns.

### Structural

7. **Severity escalation should require corroboration.** One signal = low/info. Two independent signals = warning. Three = critical. "No lastRunAtMs" is one signal. It should never alone trigger a critical alert.

8. **The health cron should report its own confidence level** alongside its diagnosis — e.g., *"Confidence: LOW — only 1 of 3 failure indicators present."*

---

## Lessons

- **Absence of data ≠ evidence of failure.** Agents must be explicitly taught this. Prompt design must close the vocabulary gap between "never fired" and "stopped firing."
- **A monitoring system that lists crons successfully cannot be experiencing a gateway failure.** Self-contradiction in a diagnosis is a red flag; agents need to check for it.
- **Playbooks must include false-alarm patterns**, not just real failure patterns. If the only entries describe real failures, the agent will search for a real failure to match — and find one, even when none exists.
- **Recommendations carry weight.** An agent recommending "restart the gateway" during an active user session is recommending something disruptive. High-disruption recommendations require high evidence bars.

---

*Filed by: subagent (post-mortem-analysis session)*
*Triggered by: 2026-02-23 System Health false alarm*
*Related files: ~/Master/task-system/error-handling/cron-errors.md (entry #6)*
