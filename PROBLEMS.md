# PROBLEMS.md — Known Issues & Unsolved Problems

*Prevents re-discovering the same problems. Tracks what we've tried.*

## Active Problems

### Statefulness-Capability Tradeoff
- **Problem:** Claude web has best reasoning + artifacts but is stateless. Stateful tools sacrifice capability.
- **Impact:** Strategic thinking in Claude web, execution elsewhere, context lost in between.
- **Mitigation:** /master repo as coordination layer + manual bridging.
- **Watch for:** Claude Desktop MCP, OneContext maturity.

### Context Fragmentation Across Tools
- **Problem:** Work in one tool invisible to others. Leads to restarting completed work.
- **Mitigation:** STATUS.md, claude-mem (when installed).
- **Ideal:** Cross-tool context protocol.

### Complex Ontology Embedding
- **Problem:** How to store/retrieve interconnected knowledge (depth psychology × biology) without loading huge context.
- **Status:** Unsolved. On-demand loading works for simple domains, not interconnected knowledge.
- **Ideas:** Knowledge graph DB, semantic chunking, compiled rule extraction.

### Cowork VM Disk Limits
- **Problem:** Tiny VM fills up with MCP dependencies.
- **Fix:** Remove heavy MCPs (academic-research-server was culprit).
- **Root cause:** Product limitation — disk not configurable.

### Pre-Revenue Chicken-and-Egg
- **Problem:** Many business processes can't be validated without clients. Can't get clients without processes.
- **Mitigation:** Build minimum viable versions of critical-path processes first.

## Resolved

| Problem | Solution | Date |
|---------|----------|------|
| ClawdBot boot payload (~15k tokens) | File restructure → ~1.5k tokens | 2026-02-09 |
| ClawdBot not working with Opus 4.6 | OpenClaw update + file rewrite | 2026-02-09 |
| Cowork ENOSPC | Remove academic-research MCP | 2026-02-09 |
