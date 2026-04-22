# README

> <div align="center">
  <p><strong>@funkai/agents</strong></p>
  <p>Lightweight workflow and agent orchestration framework built on the <a href="https:

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
<div align="center">
  <p><strong>@funkai/agents</strong></p>
  <p>Lightweight workflow and agent orchestration framework built on the <a href="https://github.com/vercel/ai">Vercel AI SDK</a>.</p>

<a href="https://www.npmjs.com/package/@funkai/agents"><img src="https://img.shields.io/npm/v/@funkai/agents" alt="npm version" /></a>
<a href="https://github.com/joggrdocs/funkai/blob/main/LICENSE"><img src="https://img.shields.io/github/license/joggrdocs/funkai" alt="License" /></a>

</div>

## Features

- :zap: **Functions all the way down** — `agent`, `tool`, `workflow` are functions that return plain objects.
- :jigsaw: **Composition over configuration** — Combine small pieces instead of configuring large ones.
- :shield: **Result, never ~~panic~~ throw** — Every public method returns `Result<T>`. Pattern-match on `ok` instead of try/catch.
- :lock: **Closures are state** — Workflow state is just `let` variables in your handler.
- :mag: **`$` is optional sugar** — The `$` helpers register data flow for observability; plain imperative code works too.

## Install

```bash
npm install @funkai/agents
```

## Usage

### Agent

```ts
import { agent } from "@funkai/agents";
import { openai } from "@ai-sdk/openai";

const helper = agent({
  name: "helper",
  model: openai("gpt-4.1"),
  system: "You are a helpful assistant.",
});

const result = await helper.generate({ prompt: "What is TypeScript?" });

if (!result.ok) {
  console.error(result.error.code, result.error.message);
} else {
  console.log(result.output);
}
```

### Tool

```ts
import { tool } from "@funkai/agents";
import { z } from "zod";

const fetchPage = tool({
  description: "Fetch the contents of a web page by URL",
  inputSchema: z.object({ url: z.url() }),
  execute: async ({ url }) => {
    const res = await fetch(url);
    return { url, status: res.status, body: await res.text() };
  },
});
```

### Flow Agent

```ts
import { flowAgent } from "@funkai/agents";
import { z } from "zod";

const research = f

*[truncated — see source for full prompt]*