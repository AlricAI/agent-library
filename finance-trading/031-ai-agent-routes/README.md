# 031 Ai Agent Routes

> ## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 031 — AI Routes (AI Chat, Agents, Embeddings)

## Preamble — Read Every Time

You are an expert TypeScript engineer building **cryptocurrency.cv**. Stack: **Hono + TypeScript + Node.js**, Google Cloud Run, Redis caching, Zod validation.

### Absolute Rules

1. **Never mock, stub, or fake anything.** 2. **TypeScript strict mode** — no `any`. 3. **Always kill terminals** after every command. 4. **Commit and push as `nirholas`.** 5. **If close to hallucinating — tell the prompter.** 6. **Run `npx tsc --noEmit` and `npx vitest run`.** 7. **Improve any existing code you touch.**

---

## Task

Build / improve `src/routes/ai.ts` and `src/routes/agents.ts` — AI-powered crypto analysis, agent orchestration, and AI chat endpoints.

### Source Imports

```typescript
// ai.ts
import { Hono } from 'hono';
import * as ai from '../lib/ai.js';
import * as agents from '../lib/agents.js';
import { ApiError } from '../lib/api-error.js';

export const aiRoutes = new Hono();

// agents.ts
import { Hono } from 'hono';
import { loadAgent, listAgents, runAgent } from '../lib/agents.js';
import { ApiError } from '../lib/api-error.js';

export const agentRoutes = new Hono();
```

### AI Endpoints

| Method | Path | Description |
|--------|------|-------------|
| POST | `/chat` | AI chat with crypto context |
| POST | `/analyze` | AI market analysis for a coin/topic |
| POST | `/summarize` | Summarize crypto news/articles |
| POST | `/sentiment` | AI-powered sentiment analysis |
| POST | `/strategy` | Generate trading/DeFi strategy |
| POST | `/explain` | Explain crypto concepts for beginners |
| GET | `/models` | Available AI models |
| POST | `/embed` | Generate text embeddings |
| POST | `/compare` | AI comparison of protocols/tokens |
| POST | `/risk-assessment` | AI-generated risk assessment |
| POST | `/portfolio-review` | AI portfolio analysis |

### Agent Endpoints

| Method | Path | Description |
|--------|------|-------------|
| GET | `/list` | List all available agents |


*[truncated — see source for full prompt]*