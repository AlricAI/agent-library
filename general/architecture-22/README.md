# Architecture

> ## Package dependency graph

```mermaid
graph TD
    agents["@funkai/agents"]
    models["@funkai/models"]
    prompts["@funkai/prompts"]
    cli["@fu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Architecture

## Package dependency graph

```mermaid
graph TD
    agents["@funkai/agents"]
    models["@funkai/models"]
    prompts["@funkai/prompts"]
    cli["@funkai/cli"]
    ai["ai (Vercel AI SDK)"]

    agents --> models
    agents --> ai
    cli --> prompts
    models --> ai
```

- **`@funkai/agents`** depends on `@funkai/models` (for `ProviderRegistry` type) and `ai` (Vercel AI SDK).
- **`@funkai/models`** depends on `ai` for the `LanguageModel` type. Standalone otherwise.
- **`@funkai/prompts`** is fully standalone -- no dependency on other funkai packages.
- **`@funkai/cli`** depends on `@funkai/prompts` for prompt generation and linting.

## Agent

`agent()` wraps the AI SDK's `generateText` and `streamText` with:

- **Typed input** -- Optional Zod schema + prompt template. When provided, `.generate()` accepts typed input and validates it before calling the model. In simple mode, raw strings or message arrays pass through directly.
- **Tools** -- A record of `tool()` instances exposed to the model for function calling.
- **Subagents** -- Other agents passed via the `agents` config, automatically wrapped as callable tools with abort signal propagation.
- **Hooks** -- `onStart`, `onFinish`, `onError`, `onStepFinish` for observability. Per-call overrides merge with base hooks.
- **Result** -- Every method returns `Result<T>`. Success fields are flat on the object. Errors carry `code`, `message`, and optional `cause`.

The tool loop runs up to `maxSteps` iterations (default 20), where each iteration may invoke tools or subagents before producing a final response.

## FlowAgent

`flowAgent()` provides code-driven orchestration. The handler receives `{ input, $, log }`:

- **`input`** -- Validated against the input Zod schema.
- **`$`** (StepBuilder) -- Traced operations: `$.step()`, `$.agent()`, `$.map()`, `$.each()`, `$.reduce()`, `$.while()`, `$.all()`, `$.race()`. Each call becomes an entry in the execution trace.
- **`log`** -- Scoped logger with context

*[truncated — see source for full prompt]*