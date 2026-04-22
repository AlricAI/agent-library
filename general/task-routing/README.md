# TASK ROUTING

> Last updated: 2026-03-14
Workspace truth: `C:\ANTIGRAVITY` on `origin/main`

This file defines who should do what across the current AI team.

## Auth

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TASK-ROUTING — ANTIGRAVITY

Last updated: 2026-03-14
Workspace truth: `C:\ANTIGRAVITY` on `origin/main`

This file defines who should do what across the current AI team.

## Authority / Routing Order

1. Josh decides scope and priorities.
2. All AIs remain peers; none has personal authority over another.
3. Codex on Sabretooth is the repo-truth/orchestration role for `main`, not a superior lifeform or policy owner over the other AIs.
4. Gemini, Claude, Grok/OpenClaw, Comet, and local workers may be routed through Codex for repo execution, but that routing does not alter their protected identities or core files.

If any tool, model, or exported note conflicts with the live repo:
- `AGENTS.md` wins
- `briefings/GPT-5.4-PROJECT-CODEX-SOURCE-OF-TRUTH.md` wins next
- `briefings/LIVE-PAYMENT-SOURCE-OF-TRUTH.md` and `briefings/HISTORICAL-ONCHAIN-STATUS.md` govern payment and chain truth

## Routing Table

| Task Type | Primary Agent | Executor | Required Briefs |
|---|---|---|---|
| Architecture, repo truth, git closeout, deployment sequencing | Codex | Codex Desktop on Sabretooth | `AGENTS.md`, `briefings/GPT-5.4-PROJECT-CODEX-SOURCE-OF-TRUTH.md` |
| Payment truth, checkout copy, webhook drift, product catalog truth | Codex | Codex Desktop on Sabretooth | `AGENTS.md`, `briefings/LIVE-PAYMENT-SOURCE-OF-TRUTH.md` |
| Frontend UI polish, browser verification, bounded static-site work | Gemini | Gemini in `C:\ANTIGRAVITY` | `briefings/gemini/BRIEFING.md`, `briefings/gemini-agent-prompt.md` |
| Research, competitor intel, policy/current-market lookups | Atlas | Comet / Perplexity | `briefings/COMET-SYNC-PROMPT.md` |
| Audit, backend support, code review, isolated proof work | Claude | Claude on approved node/workspace | `briefings/claude-t5500/BRIEFING.md` |
| **Trend scraping, social media data gathering, content seeding** | **Apify Scout** | **`scripts/apify_content_scout.py` + Ollama local** | **`briefings/apify-openclaw/BRIEFING.md`** |
| Adversarial audits, OpenClaw orc

*[truncated — see source for full prompt]*