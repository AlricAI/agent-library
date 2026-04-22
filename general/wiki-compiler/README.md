# WIKI COMPILER

> End-to-end reference for how the wiki compiler works today: entry points, agent pipeline, prompts, tools, persistence, concurrency, and error handling.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Wiki Compiler — Architecture & Flow

End-to-end reference for how the wiki compiler works today: entry points, agent pipeline, prompts, tools, persistence, concurrency, and error handling. Everything below is grounded in the current code under `apps/server/src/` and `packages/db/src/` (no speculation).

---

## 1. The 30-second picture

Three specialised agents run inside one orchestrator. Each is an `ai` SDK `generateText` call with `gpt-4o-mini`, a system prompt, and a bounded tool set:

| Agent | Role | Writes? | Tools | Called by |
|-------|------|---------|-------|-----------|
| **Curator** | Organize: create spaces, assign entries, maintain hierarchy, update index | yes (spaces, M2Ms, index page) | 7 tools | Orchestrator — twice per compile |
| **Writer** | Synthesize: write/update wiki pages per space | yes (wiki_pages, versions, M2M) | 5 tools | Orchestrator — one per "dirty" space, up to 3 in parallel |
| **Linter** | Health-check: flag orphans / thin pages / duplicates | no (only `agent_logs`) | 4 tools | Separate entrypoint `runWikiLint` |

```mermaid
flowchart LR
  A[Mobile app] -- wiki.compile --> B[wikiRouter]
  A -. wiki.lint .-> B
  B --> C[wikiService.compile]
  C --> D[runWikiCompile]
  D --> E((Orchestrator))

  E --> F[Curator • initial]
  F --> G[Writer × N<br/>parallel ≤3]
  G --> H[Curator • finalize]

  E -.lint path.-> I[runWikiLint]
  I --> J[Linter]

  F & G & H & J --> K[(Postgres)]
  F & G & H & J --> L[(agent_logs)]

  subgraph Optional async path
    M[wikiCompileTask<br/>Trigger.dev] --> D
    N[wikiLintTask<br/>Trigger.dev] --> I
  end
```

The Trigger.dev tasks exist but are **not currently invoked** from the HTTP path — every compile today runs synchronously inside the HTTP request. The tasks are there for future auto-compile (see `docs/tickets/wiki-agent/T-015p-auto-compile-infrastructure.md`, deferred).

---

## 2. Entry points

All file paths are relative to the monorepo root.

### HTTP (oRPC) — `apps/server/src/router/wiki.ro

*[truncated — see source for full prompt]*