# Create Flow Agent

> `flowAgent()` creates a `FlowAgent` from a configuration object and an imperative handler function.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Create a Flow Agent

`flowAgent()` creates a `FlowAgent` from a configuration object and an imperative handler function. The handler IS the flow agent — no step arrays, no definition objects. State is just variables. `$` is passed in for tracked operations.

## Basic flow agent

A flow agent has a typed `input` Zod schema and an optional `output` Zod schema, plus a handler function. The handler receives validated input and a `$` step builder for tracked operations.

```ts
import { flowAgent } from "@funkai/agents";
import { z } from "zod";

const myFlowAgent = flowAgent(
  {
    name: "data-processor",
    input: z.object({ url: z.url() }),
    output: z.object({ title: z.string(), wordCount: z.number() }),
  },
  async ({ input, $ }) => {
    const page = await $.step({
      id: "fetch-page",
      execute: async () => {
        const res = await fetch(input.url);
        return await res.text();
      },
    });

    if (!page.ok) throw new Error(page.error.message);

    return {
      title: input.url,
      wordCount: page.output.split(/\s+/).length,
    };
  },
);

const result = await myFlowAgent.generate({ input: { url: "https://example.com" } });
if (result.ok) {
  console.log(result.output); // validated output
  console.log(result.trace); // frozen execution trace tree
  console.log(result.usage); // aggregated token usage from all $.agent() calls
  console.log(result.duration); // wall-clock time in ms
}
```

## `$` operations

Every `$` method is registered in the execution trace and returns a `FlowStepResult<T>`. Always check `.ok` before accessing `.output`.

```ts
if (result.ok) {
  console.log(result.output); // the step's return value
  console.log(result.duration); // wall-clock time in ms
} else {
  console.error(result.error.message);
  console.error(result.error.stepId);
}
```

### `$.step` — single unit of work

The fundamental tracked operation. The `execute` callback receives a nested `$` for further composition.

```ts
const result = awa

*[truncated — see source for full prompt]*