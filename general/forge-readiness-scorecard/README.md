# FORGE READINESS SCORECARD

> **Target: A+ across the board before first real agent run.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCM Forge Readiness Scorecard

**Target: A+ across the board before first real agent run.**
**Last audited: 2026-04-04**

---

## CORE ENGINE

| # | Feature | Grade | Notes | Fix |
|---|---------|-------|-------|-----|
| 1 | Heartbeat lifecycle (wake/work/sleep) | B | Dry-run validated, no live test | Live test with real CLI |
| 2 | Claude CLI adapter | B+ | E2E validated once, auth expired | Re-auth + re-test |
| 3 | Gemini CLI adapter | C | Code exists, zero runtime testing | Test on Mini |
| 4 | Codex CLI adapter | C | Code exists, zero runtime testing | Test on Mini |
| 5 | Run executor (poll/claim/spawn) | B+ | Validated, 3 column bugs fixed | Stress test |
| 6 | Session resume/rotate | C | Basic implementation, untested | Test session persistence |
| 7 | Cron routine scheduler | B | Built, column bugs fixed | Live test with one routine |
| 8 | Issue assignment wakeup | B | Dry-run validated | Live test |
| 9 | @-mention wakeups | D | Parser built, NOT wired to run | Wire mention → wakeup in comment handler |
| 10 | Orphan reaper | B | Built, untested edge cases | Verify with stuck run |
| 11 | Git worktree isolation | C | Built, untested | Test worktree create/cleanup |
| 12 | Cost tracking | B | Records costs, no budget enforcement | Add auto-pause at budget limit |
| 13 | Concurrent run limiting | B | MAX_CONCURRENT_RUNS=3, per-adapter not enforced | Add per-adapter slot tracking |

## AGENT QUALITY

| # | Feature | Grade | Notes | Fix |
|---|---------|-------|-------|-----|
| 14 | AGENTS.md per agent (MCM Forge) | A | 4/4 done | — |
| 15 | AGENTS.md per agent (DirtSync) | F | 39 agents, zero instructions | Create AGENTS.md for each on migration |
| 16 | HEARTBEAT.md protocol | A | 4/4 done | — |
| 17 | SOUL.md personality | A | 4/4 done | — |
| 18 | TOOLS.md reference | A | 4/4 done | — |
| 19 | Prompt injects ALL 4 files | F | Only AGENTS.md via --append-system-prompt-file | Inject HEARTBEAT+SOUL+TOOLS into prompt template |
| 20 | Skills wired to agents

*[truncated — see source for full prompt]*