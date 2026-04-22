# Flow Agent

> `flowAgent()` creates a `FlowAgent` from a configuration object and an imperative handler function.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# flowAgent()

`flowAgent()` creates a `FlowAgent` from a configuration object and an imperative handler function. The handler IS the flow agent -- no step arrays, no definition objects. State is just variables. `$` is passed in for tracked operations.

## Signature

```ts
function flowAgent<TInput, TOutput>(
  config: FlowAgentConfig<TInput, TOutput>,
  handler: FlowAgentHandler<TInput, TOutput>,
): FlowAgent<TInput, TOutput>;
```

## FlowAgentConfig

| Field          | Required | Type                                                            | Description                                   |
| -------------- | -------- | --------------------------------------------------------------- | --------------------------------------------- |
| `name`         | Yes      | `string`                                                        | Unique flow agent name (used in logs, traces) |
| `input`        | Yes      | `ZodType<TInput>`                                               | Zod schema for validating input               |
| `output`       | Yes      | `ZodType<TOutput>`                                              | Zod schema for validating output              |
| `logger`       | No       | `Logger`                                                        | Pino-compatible logger                        |
| `onStart`      | No       | `(event: { input }) => void \| Promise<void>`                   | Hook: fires when the flow agent starts        |
| `onFinish`     | No       | `(event: { input, output, duration }) => void \| Promise<void>` | Hook: fires on success                        |
| `onError`      | No       | `(event: { input, error }) => void \| Promise<void>`            | Hook: fires on error                          |
| `onStepStart`  | No       | `(event: StepStartEvent) => void \| Promise<void>`              | Hook: fires when any `$` step starts          |
| `onStepFinish` | No       | `(event: StepFinishEvent) => void \| Promise<void>`             | Hook: f

*[truncated — see source for full prompt]*