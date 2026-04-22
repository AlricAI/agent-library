# 14 Backend Ai Agents

> ## Context

You are working on the AI and agent orchestration system in crypto-vision. The system has:

- `src/lib/ai.ts` — Multi-provider AI client: 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 14 — Backend: AI/Agents Orchestration System

## Context

You are working on the AI and agent orchestration system in crypto-vision. The system has:

- `src/lib/ai.ts` — Multi-provider AI client: Groq → Gemini → OpenAI → Anthropic → OpenRouter
- `src/lib/agents.ts` — Agent execution engine
- `src/lib/orchestrator.ts` — Multi-agent orchestration
- `src/lib/rag.ts` — Retrieval-Augmented Generation
- `src/lib/embeddings.ts` — Text embedding generation
- `src/lib/vector-store.ts` — Vector similarity search
- `src/lib/search.ts` — Semantic search
- `src/routes/agents.ts` — Agent API endpoints
- `src/routes/ai.ts` — AI inference endpoints
- `src/routes/search.ts` — Search endpoints
- `agents/src/` — 43 JSON agent definitions (prompts, tools, config)

## Task

### 1. Complete the AI Provider Chain (`src/lib/ai.ts`)

Ensure the multi-provider fallback chain works:

```typescript
// Provider chain: Groq → Gemini → OpenAI → Anthropic → OpenRouter
//
// Each provider:
//   1. Check API key exists in env
//   2. Attempt inference with timeout (10s for Groq, 30s for others)
//   3. On failure → fall through to next provider
//   4. Log which provider was used and latency
//
// Methods:
//   generateText(prompt, options?) — Simple text generation
//   generateJSON<T>(prompt, schema: ZodSchema<T>) — Structured output with validation
//   generateEmbedding(text) — Text → vector (use same provider chain)
//   streamText(prompt, options?) — Streaming response
//
// Environment variables:
//   GROQ_API_KEY, GOOGLE_GEMINI_API_KEY, OPENAI_API_KEY,
//   ANTHROPIC_API_KEY, OPENROUTER_API_KEY
//
// Provider-specific configs:
//   Groq: model "llama-3.3-70b-versatile", fast but limited context
//   Gemini: model "gemini-2.0-flash", good for structured output
//   OpenAI: model "gpt-4o-mini", reliable
//   Anthropic: model "claude-sonnet-4-20250514", best quality
//   OpenRouter: model "meta-llama/llama-3.1-70b-instruct", cheapest fallback
```

### 2. Complete Agent Execution (`src/

*[truncated — see source for full prompt]*