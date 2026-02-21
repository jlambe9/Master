# Global Infrastructure Checklist

*Pre-flight check. Run daily at 05:00 (CLAWD-005) before any cron fires.*
*Any failure here blocks ALL automated operations.*

## Core Runtime
- [ ] OpenClaw gateway running (`openclaw gateway status`)
- [ ] Main session responsive
- [ ] Cron scheduler active (`cron status`)
- [ ] Sub-agent spawning functional

## API Access
- [ ] Anthropic API — auth valid, not rate-limited
- [ ] Google/Gemini API — key valid
- [ ] xAI/Grok API — key valid (fallback model)

## External Services
- [ ] Expandi API — returns data (`node scripts/expandi-status.js`)
- [ ] PhantomBuster — agents accessible
- [ ] H1 Google Sheet — read/write functional
- [ ] Gmail/IMAP — connection alive
- [ ] Neo4J — connection alive, queries working

## Browser
- [ ] Chrome (clawd profile) — CDP connection on port 18800
- [ ] Can navigate to a test URL
- [ ] LinkedIn session not expired (check via snapshot)

## Repos & Storage
- [ ] ~/Master — `git pull` and `git push` both work
- [ ] ~/clawd — workspace readable/writable
- [ ] Memory files — `memory/` directory accessible

## Remote Recovery
- [ ] SSH to Mac Mini accessible (if configured)
- [ ] Tailscale or alternative remote access (if configured)
- [ ] Gateway restart command documented and tested

## Failure → Fallback Matrix
| Failure | Impact | Self-Heal | Fallback | Escalate |
|---------|--------|-----------|----------|----------|
| Anthropic API down | Main session, Opus sub-agents | — | Switch to Gemini/Grok | Auto |
| Gemini API down | Default model, cheap sub-agents | — | Switch to Anthropic | Auto |
| Both LLM APIs down | Everything | — | — | Alert Jamie immediately |
| Expandi API down | Health check, sync | — | Browser scrape | Alert if >4h |
| H1 Sheet down | All outreach data | — | Cache last read | Alert Jamie |
| Browser crash | LinkedIn research, Expandi dashboard | `browser start profile=clawd` | Skip browser tasks | Alert if restart fails |
| Gateway crash | All sessions, all crons | `openclaw gateway restart` | — | Alert Jamie for manual restart |
| Git push fails | Master repo sync | Auth refresh | Queue pushes | Alert Jamie |
