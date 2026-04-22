# ISSUES AND ROADMAP

> Single source of truth for issue status and development phases.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Findash GitHub Issues & Roadmap

Single source of truth for issue status and development phases.

---

## Phase checklist

| Phase | Status | Description |
|-------|--------|-------------|
| **Phase 1** | ✅ Done | Core app (FastAPI + Next.js), Command Center, Dashboard, account cards, agent panels (M1/M4/M9/M11), CI/CD workflow |
| **Phase 2** | In progress | Dashboard real data (#8); remaining bot/execution work (#10). [#3](https://github.com/massoudsh/Findash/issues/3) closed. |
| **Phase 3** | TBD | Scale, observability, E2E tests, production hardening |

---

## Closed issues (summary)

- **#2** – ui: Dashboard account cards and green fintech theme → Closed. Account cards responsive/accessible, loading/error states, glass/green theme applied.
- **#4** – ci: Harden CI/CD and add optional deploy → Closed. Frontend build in CI, workflow comments, deploy placeholders.
- **#5** – docs/llm: Document open-source and free LLM usage → Closed. LLM docs + env.example; `GET /llm/status` and Reports page `LlmStatusBadge`.
- **#6** – ops: Docker core stack and optional LLM profile → Closed. README core vs `--profile llm`, Redis 6380, `scripts/healthcheck-core.sh`, production override note.
- **#3** – feat: Trading bots execution and agent panels integration → Closed. Bot CRUD/start/pause/stop with optional auth; stub API for M1/M4/M9/M11 panels; panels wired to backend with mock fallback; start response includes execution_mode (paper/live).

---

## Open issues (current)

| # | Title | Priority |
|---|--------|----------|
| [8](https://github.com/massoudsh/Findash/issues/8) | ui: Dashboard real data wiring and API timeouts | Medium |
| [9](https://github.com/massoudsh/Findash/issues/9) | feat: Technical page – wire Screener, Watchlist, Economic Calendar | Low |
| [10](https://github.com/massoudsh/Findash/issues/10) | feat: Trading bots execution – wire backend and run on platform | High |
| [11](https://github.com/massoudsh/Findash/issues/11) | docs: Development roadmap and

*[truncated — see source for full prompt]*