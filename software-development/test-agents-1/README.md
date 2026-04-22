# Test Agents

> Patterns for unit testing agents, flow agents, and tools with mocked models and deterministic assertions.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Test Agents and Flow Agents

Patterns for unit testing agents, flow agents, and tools with mocked models and deterministic assertions.

## Prerequisites

- `@funkai/agents` installed
- Vitest configured (`pnpm test --filter=@funkai/agents`)
- Familiarity with `agent()`, `flowAgent()`, and `tool()` APIs

## Steps

### 1. Use per-call model overrides for integration smoke tests

Agents accept a `model` override on each `.generate()` call. This is useful for low-cost integration smoke tests. For deterministic unit tests, use a fixed mock model/test double.

```ts
import { agent } from "@funkai/agents";
import { openai } from "@ai-sdk/openai";
import { z } from "zod";
import { describe, it, expect } from "vitest";
import { simulateReadableStream } from "ai";

const summarizer = agent({
  name: "summarizer",
  model: openai("gpt-4.1"),
  input: z.object({ text: z.string() }),
  prompt: ({ input }) => `Summarize:\n\n${input.text}`,
});

describe("summarizer", () => {
  it("returns a summary", async () => {
    // Create a mock model that returns a fixed response
    const mockModel = {
      doGenerate: async () => ({
        text: "This is a fixed test summary",
        finishReason: "stop",
        usage: { promptTokens: 10, completionTokens: 5 },
      }),
    };

    const result = await summarizer.generate(
      { text: "Long article content..." },
      { model: mockModel as any },
    );

    expect(result.ok).toBe(true);
    if (result.ok) {
      expect(result.output).toBe("This is a fixed test summary");
    }
  });
});
```

### 2. Assert on Result shape

Every agent and flow agent returns `Result<T>`. Test both success and error paths by checking `result.ok`.

```ts
import { agent } from "@funkai/agents";
import { openai } from "@ai-sdk/openai";
import { describe, it, expect } from "vitest";

const helper = agent({
  name: "helper",
  model: openai("gpt-4.1"),
  system: "You are a helpful assistant.",
});

describe("helper", () => {
  it("succeeds with a str

*[truncated — see source for full prompt]*