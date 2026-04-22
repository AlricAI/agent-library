# Error Recovery

> Patterns for building resilient agents and flow agents that recover gracefully from failures.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Error Recovery

Patterns for building resilient agents and flow agents that recover gracefully from failures.

## Prerequisites

- `@funkai/agents` installed
- Familiarity with `flowAgent()`, `$.step`, `$.while`, `$.map`, and hooks
- Understanding of `FlowStepResult` and `Result` types

## Steps

### 1. Use fallback values on step failure

Every `$` method returns `FlowStepResult<T>` with an `ok` field. Check it before accessing `.output` and provide a fallback when the step fails.

```ts
import { flowAgent } from "@funkai/agents";
import { z } from "zod";

const resilient = flowAgent(
  {
    name: "resilient-fetch",
    input: z.object({ url: z.string() }),
    output: z.object({ body: z.string(), source: z.string() }),
  },
  async ({ input, $ }) => {
    const primary = await $.step({
      id: "fetch-primary",
      execute: async () => {
        const res = await fetch(input.url);
        if (!res.ok) throw new Error(`HTTP ${res.status}`);
        return await res.text();
      },
    });

    if (primary.ok) {
      return { body: primary.output, source: "primary" };
    }

    // Fallback to a cached or default value
    const fallback = await $.step({
      id: "fetch-fallback",
      execute: async () => {
        const res = await fetch(`${input.url}?cached=true`);
        return await res.text();
      },
    });

    return {
      body: fallback.ok ? fallback.output : "Service unavailable",
      source: fallback.ok ? "fallback" : "default",
    };
  },
);
```

### 2. Retry with `$.while`

Use `$.while` for retry logic with a bounded iteration count.

```ts
import { flowAgent } from "@funkai/agents";
import { z } from "zod";

const retryable = flowAgent(
  {
    name: "retry-fetch",
    input: z.object({ url: z.string(), maxRetries: z.number().default(3) }),
    output: z.object({ body: z.string(), attempts: z.number() }),
  },
  async ({ input, $ }) => {
    const result = await $.while({
      id: "retry-loop",
      condition: ({ value, index }) =

*[truncated — see source for full prompt]*