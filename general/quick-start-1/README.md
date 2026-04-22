# Quick Start

> ## Installation

```bash
pnpm add @funkai/agents @ai-sdk/openai
```

Set your API key:

```bash
export OPENAI_API_KEY=sk-...
```

## 1. Create a simpl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Quick Start

## Installation

```bash
pnpm add @funkai/agents @ai-sdk/openai
```

Set your API key:

```bash
export OPENAI_API_KEY=sk-...
```

## 1. Create a simple agent

```typescript
import { agent } from "@funkai/agents";
import { openai } from "@ai-sdk/openai";

const assistant = agent({
  name: "assistant",
  model: openai("gpt-4.1"),
  system: "You are a helpful assistant.",
});

const result = await assistant.generate({ prompt: "What is TypeScript?" });

if (!result.ok) {
  console.error(result.error.code, result.error.message);
  process.exit(1);
}

console.log(result.output);
// result.usage.totalTokens, result.messages, result.finishReason
```

## 2. Add tools

```typescript
import { agent, tool } from "@funkai/agents";
import { openai } from "@ai-sdk/openai";
import { z } from "zod";

const fetchPage = tool({
  description: "Fetch a web page by URL",
  inputSchema: z.object({ url: z.string().url() }),
  execute: async ({ url }) => {
    const res = await fetch(url);
    return { status: res.status, body: await res.text() };
  },
});

const researcher = agent({
  name: "researcher",
  model: openai("gpt-4.1"),
  system: "You research topics by fetching web pages.",
  tools: { fetchPage },
});

const result = await researcher.generate({ prompt: "Summarize https://example.com" });

if (result.ok) {
  console.log(result.output);
}
```

## 3. Multi-step orchestration with flowAgent

```typescript
import { agent, flowAgent } from "@funkai/agents";
import { openai } from "@ai-sdk/openai";
import { z } from "zod";

const writer = agent({
  name: "writer",
  model: openai("gpt-4.1"),
  input: z.object({ topic: z.string() }),
  prompt: ({ input }) => `Write a short explanation of: ${input.topic}`,
});

const reviewer = agent({
  name: "reviewer",
  model: openai("gpt-4.1"),
  input: z.object({ draft: z.string() }),
  prompt: ({ input }) => `Review and improve this text:\n\n${input.draft}`,
});

const pipeline = flowAgent(
  {
    name: "write-and-review",
    in

*[truncated — see source for full prompt]*