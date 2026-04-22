# Cost Tracking

> Track token usage, calculate costs, enforce budgets, and optimize model selection for cost-efficient agents and flow agents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Cost Tracking

Track token usage, calculate costs, enforce budgets, and optimize model selection for cost-efficient agents and flow agents.

## Prerequisites

- `@funkai/agents` installed
- `@funkai/models` installed (provides `calculateCost`, `model`, `models`)

## Track usage per agent call

Every successful `agent.generate()` returns `result.usage` with resolved token counts. All fields are `number` (0 when the provider does not report a field).

```ts
import { agent } from "@funkai/agents";
import { openai } from "@ai-sdk/openai";

const helper = agent({
  name: "helper",
  model: openai("gpt-4.1"),
  system: "You are a helpful assistant.",
});

const result = await helper.generate({ prompt: "What is TypeScript?" });

if (result.ok) {
  console.log("Input tokens:", result.usage.inputTokens);
  console.log("Output tokens:", result.usage.outputTokens);
  console.log("Total tokens:", result.usage.totalTokens);
  console.log("Cache read:", result.usage.cacheReadTokens);
  console.log("Cache write:", result.usage.cacheWriteTokens);
  console.log("Reasoning:", result.usage.reasoningTokens);
}
```

## Calculate cost with `@funkai/models`

Use `calculateCost()` to convert token counts into USD amounts. Look up model pricing with `model()`.

```ts
import { agent } from "@funkai/agents";
import { openai } from "@ai-sdk/openai";
import { calculateCost, model } from "@funkai/models";

const summarizer = agent({
  name: "summarizer",
  model: openai("gpt-4.1"),
  system: "You produce concise summaries.",
});

const result = await summarizer.generate({ prompt: "Summarize the history of TypeScript." });

if (result.ok) {
  const modelDef = model("gpt-4.1");
  if (!modelDef) {
    return;
  }

  const cost = calculateCost(result.usage, modelDef.pricing);

  console.log("Input cost:", `$${cost.input.toFixed(6)}`);
  console.log("Output cost:", `$${cost.output.toFixed(6)}`);
  console.log("Cache read cost:", `$${cost.cacheRead.toFixed(6)}`);
  console.log("Cache write cost:", `

*[truncated — see source for full prompt]*