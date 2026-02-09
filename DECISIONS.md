# DECISIONS.md — Cross-Tool Decision Log

*Newest first. Format: what, why, where, what it supersedes.*

## 2026-02-09

- **BOSS system: boss/ directory in /master with sub-files per business domain** (Claude web)
  Goals + KPIs live in BOSS.md. STATUS.md stays daily tactical only.
  Domain repos have operational detail. boss/ has strategic overview + links.
  Sync via linking, not duplication. Future: cron to validate links.

- **Domain nesting: domains/business/ replaced by boss/** (Claude web)
  Business domains live in boss/. Non-business in domains/research/, domains/personal/, domains/ai/.

- **Skills need a registry with KPI links and "does it actually work" tracking** (Claude web)
  SKILLS.md tracks: status, process it supports, KPI it impacts, last verified, evidence.

- **ClawdBot to self-restructure** (Claude web)
  Feed rewrite doc directly. ClawdBot archives originals and deploys.

- **Cowork ENOSPC: academic-research MCP server** (Claude web)
  Removed it. Cowork boots clean now.

## 2026-02-08

- **Git repo as coordination layer** (Claude web)
  Over Google Doc. Cursor/Claude Code read natively. ClawdBot git pull/push.
  Tradeoff: Claude web can't write directly (bridge via GitHub app).

- **claude-mem for Cursor sessions only** (Claude web)
  Won't bridge to ClawdBot or Claude web. Install on Mac Mini.
