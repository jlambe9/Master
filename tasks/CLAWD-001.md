# CLAWD-001 — Fix Overnight Failure Cascade (Error Handling & Resilience)

> **Summary:** One Anthropic rate limit killed all automation for 8+ hours. No backoff, no recovery, no fallback. Need circuit breakers and non-Anthropic escape hatch.

**Domain:** clawd/reliability
**Priority:** 🔴 CRITICAL
**Status:** DECOMPOSED
**Type:** EXPLOIT
**Cat:** 🟠 M
**Owner:** 🤖 Rich
**Next Action:** Add non-Anthropic fallback model (step 1) — Google Gemini key already configured
**Created:** 2026-02-11
**Pipeline:** v1.2

## Win State
Overnight automation runs reliably. A single rate limit event does NOT cascade. Zero multi-hour failures.
**Outputs (completion gate — ALL must exist to mark done):**
1. ⚠️ REVIEW — outputs not yet defined

## Root Cause
Trigger: Heavy usage → Anthropic API rate limit at 19:18 Feb 10.
Cascade: Single-provider dependency → cron jobs on main session → no backoff → stale tokens → heartbeat amplification → 8h outage.

## Subtasks
| # | Type | Task | Status | Owner | Output (proof of completion) |
|---|------|------|--------|-------|----------------------------|
| 1 | EXPLOIT | Add Gemini fallback | CAPTURED | 🤖 Rich | Config change |
| 2 | EXPLOIT | Restrict Expandi cron hours | CAPTURED | 🤖 Rich | Cron expr update |
| 3 | EXPLOIT | Isolate cron sessions | CAPTURED | 🤖 Rich | Config change |
| 4 | EXPLORE | Evaluate compaction | CAPTURED | 🤖 Rich | Test auto vs safeguard |

## Dependencies / Links
- **Upstream:** None — root reliability task
- **Downstream:** All cron-dependent tasks (BC-067, BC-DAILY-OUTREACH), overall system reliability
- **Related:** CLAWD-004 (daily scan depends on reliable crons)

## Decision Log
- 2026-02-11 04:56: Jamie flagged overnight failures. Root cause: single-provider + no backoff + main session crons.

## Execution Log
| Date | What Happened | Outcome | Duration |
|------|--------------|---------|----------|

## Outcome
| Field | Predicted | Actual |
|-------|-----------|--------|
| Category | 🟠 M | |
| Failure point | None (Rich E2E) | |
| Duration | 2h | |
| Intervention | Channel reroute (config, not code) | |
| Effectiveness | | |

---

<!-- AGENT LAYER — Jamie doesn't read below this line -->

## Layer 0 Profile (auto-scored at CAPTURED)

### 0A: Computational Structure
| Dimension | Score | Rationale |
|-----------|-------|-----------|
| Information entropy | Low | Root cause identified, fixes clear |
| Procedure specification | Specified | 4 specific config changes |
| Procedure complexity | Simple | Config edits, not code |
| Temporal delay | Immediate | Fix and test now |
| Error cost | Moderate | Bad config = new failures |
| Reward magnitude | High | Prevents 8h+ outages |
| Reward probability | Guaranteed | Config changes are deterministic |
| Value density per unit | High | Each fix prevents failure class |
| Feedback latency | Immediate | Next rate limit = test |
| Process legibility | Clear | 4 discrete changes |
| Model maturity | Familiar | Config management |
| State-tracking load | Low | 4 items checklist |

### 0B: Channel Requirements
- **Input route:** Config files (Gc,Grw) → Rich handles
- **Processing route:** Systems reasoning (Gf) → Rich handles
- **Output route:** Config edits → Rich handles
- **Channel flexible:** N/A — Rich autonomous
- **Mismatch flags:** 🟠 M — task initially requires Rich to navigate OpenClaw config (tool-specific knowledge)

### 0C: Affective Load
All dimensions: N / —

### Layer 3 Computation
- **Epistemic value:** Low
- **Pragmatic value:** High
- **Effort cost:** Low
- **Threat:** None
- **Dominant signal:** → 🟠 M (channel mismatch — OpenClaw config specifics)

### Predicted Failure Point
- **Stage:** None
- **Cause:** N/A
- **Auto-intervention:** N/A

### Version History
| Version | Date | Change | By |
|---------|------|--------|----|
| 1.0 | 2026-02-11 | Initial creation with root cause | Rich |
| 1.1 | 2026-02-21 | Reformatted to v1.1 template | Atlas |
