# Introduction

> funkai is a composable, functional TypeScript microframework for AI agent orchestration.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Introduction

funkai is a composable, functional TypeScript microframework for AI agent orchestration. It is built on the [Vercel AI SDK](https://ai-sdk.dev) -- not a replacement, but a thin layer that adds typed agents, multi-step workflows, and structured error handling on top of `generateText`/`streamText`.

## The problem

The AI SDK gives you powerful primitives like `generateText` and `streamText`. But when you start building real applications, you need more: typed agents with validated I/O, multi-step orchestration with observable traces, consistent error handling that does not rely on try/catch, and a model catalog for cost tracking. funkai adds all of this without introducing classes or hidden state.

## Two core primitives

funkai provides two agent primitives that share the same `Runnable` interface:

- **`agent()`** -- A single LLM boundary with a tool loop. Wraps `generateText`/`streamText` with typed input, tools, subagents, hooks, and `Result`-based error handling. Use this when a single model call (with optional tool iterations) is sufficient.

- **`flowAgent()`** -- Multi-step, code-driven orchestration. Your handler function receives `{ input, $, log }` where `$` is the StepBuilder providing traced operations like `$.step()`, `$.agent()`, `$.map()`, and `$.reduce()`. Use this when you need to coordinate multiple agents, run parallel work, or implement custom control flow.

Both return `Result<T>` from every public method -- a discriminated union you pattern-match on `ok` instead of catching exceptions.

## Packages

| Package           | Name    | Description                                                                   |
| ----------------- | ------- | ----------------------------------------------------------------------------- |
| `@funkai/agents`  | Agents  | Agent orchestration -- `agent()`, `flowAgent()`, `tool()`, `Result` utilities |
| `@funkai/models`  | Models  | Model catalog, provider registry, and cost calculation                

*[truncated — see source for full prompt]*