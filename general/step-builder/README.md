# Step Builder

> The `$` object is passed into every flow agent handler and step callback.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# $ StepBuilder

The `$` object is passed into every flow agent handler and step callback. It provides tracked operations that register data flow in the execution trace. Every call through `$` becomes a `TraceEntry`.

`$` is passed into every callback, enabling composition and nesting. You can always skip `$` and use plain imperative code -- it just will not appear in the trace.

## FlowStepResult

All `$` methods return `Promise<FlowStepResult<T>>`:

```ts
type FlowStepResult<T> =
  | {
      ok: true;
      output: T;
      stepId: string;
      stepOperation: OperationType;
      agentChain?: AgentChainEntry[];
      duration: number;
    }
  | {
      ok: false;
      error: StepError;
      stepId: string;
      stepOperation: OperationType;
      agentChain?: AgentChainEntry[];
      duration: number;
    };
```

Step metadata is flat on the result:

- `stepId` -- from the `$` config's `id` field
- `stepOperation` -- `'step' | 'agent' | 'map' | 'each' | 'reduce' | 'while' | 'all' | 'race'`
- `agentChain` -- optional agent ancestry chain

`StepError` extends `ResultError` with `stepId: string`.

## $.step

Single unit of work.

```ts
$.step<T>(config: StepConfig<T>): Promise<FlowStepResult<T>>
```

| Field      | Required | Type                                                         | Description                  |
| ---------- | -------- | ------------------------------------------------------------ | ---------------------------- |
| `id`       | Yes      | `string`                                                     | Unique step identifier       |
| `execute`  | Yes      | `(params: { $ }) => Promise<T>`                              | The step's logic             |
| `onStart`  | No       | `(event: { id }) => void \| Promise<void>`                   | Hook: fires when step starts |
| `onFinish` | No       | `(event: { id, result, duration }) => void \| Promise<void>` | Hook: fires on success       |
| `onError`  | No       | `(event: { id, error }) => void

*[truncated — see source for full prompt]*