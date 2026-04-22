# Hooks

> Hooks provide lifecycle callbacks for agents, flow agents, and steps.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Hooks

Hooks provide lifecycle callbacks for agents, flow agents, and steps. All hooks are optional. Hook errors are swallowed (logged via `attemptEachAsync`, never thrown) so they never mask the original error or interrupt execution.

## Agent Hooks

Set on `AgentConfig`:

| Hook           | Event fields                  | When                                                                         |
| -------------- | ----------------------------- | ---------------------------------------------------------------------------- |
| `onStart`      | `{ input }`                   | Before the model is called                                                   |
| `onFinish`     | `{ input, result, duration }` | After successful generation                                                  |
| `onError`      | `{ input, error }`            | On error, before Result is returned                                          |
| `onStepFinish` | `{ stepId }`                  | After each tool-loop step (counter-based: `agentName:0`, `agentName:1`, ...) |

## Flow Agent Hooks

Set on `FlowAgentConfig`:

| Hook           | Event fields                                                | When                                                  |
| -------------- | ----------------------------------------------------------- | ----------------------------------------------------- |
| `onStart`      | `{ input }`                                                 | After input validation, before handler runs           |
| `onFinish`     | `{ input, result, duration }`                               | After successful completion                           |
| `onError`      | `{ input, error }`                                          | On error, before Result is returned                   |
| `onStepStart`  | `StepStartEvent` (`{ stepId, stepOperation, agentChain? }`) | Before any `$` operation executes                     |
| `onStepFinish` | `StepFinishEvent`                                    

*[truncated — see source for full prompt]*