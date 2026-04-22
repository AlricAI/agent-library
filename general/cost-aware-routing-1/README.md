# Cost Aware Routing

> > **Tradução pendente** — conteúdo em inglês, aguardando tradução para pt-BR.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
> **Tradução pendente** — conteúdo em inglês, aguardando tradução para pt-BR. Contribute to [ai-dev-toolkit-pt-br](https://github.com/LucasSantana-Dev/ai-dev-toolkit-pt-br/issues).

# Cost-Aware Routing

> Token spend is a first-class observability signal. Treat cost as you would latency or error rate.

Model choice is now a cost/quality tradeoff, not a binary "do I need reasoning" decision. This pattern extends [`patterns/multi-model-routing.md`](./multi-model-routing.md) with explicit economics: token pricing, caching strategy, and output-format optimization that recovers 40-60% of spend.

## The Economics Problem

Three realities changed the game in Q1 2026:

1. **Frontier models have frontier pricing.** Opus 4 reasoning tokens cost 15x base Claude Haiku 4.5. o3-mini costs more than Sonnet per input token.
2. **Iterative workflows are expensive.** Generating prose, asking the model to reformat it, then parsing the output burns 3-5x tokens compared to schema-first design.
3. **Cache hits vary wildly by provider.** Anthropic prompt caching (TTL 5 min, automatic reuse) saves 90% of cached-segment cost; OpenAI cache hits reset on model/parameter changes; local Ollama has no cache.

The three-tier routing heuristic is still correct, but incomplete. You now need to ask: _for this task in this context, which model + format + cache strategy minimizes cost per quality unit?_

## Decision Tree: Choosing Your Model

```
Is this a one-off, low-stakes question (explain, brainstorm, summarize)?
  ├─ YES → Haiku 4.5 (1x cost, 5-10 ms latency)
  └─ NO  → continue

Does the task require extended reasoning (multi-step math, proof writing, hard logic)?
  ├─ YES → Claude Opus 4 w/ extended thinking OR o3-mini
  │         (reasoning tokens: 15-50x base cost, but 80%+ first-pass correctness)
  └─ NO  → continue

Is the task code generation, refactoring, test writing (needs context awareness)?
  ├─ YES → Claude Sonnet 4.6 or Haiku 4.5 depending on context size
  │         (Sonnet: 5-8x

*[truncated — see source for full prompt]*