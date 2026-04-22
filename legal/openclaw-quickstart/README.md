# Openclaw Quickstart

> This guide shows how to wrap an OpenClaw agent so it runs inside TraceCore's
deterministic episode harness, and how to map OpenClaw concepts to the
`r

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenClaw Quickstart (TraceCore)

This guide shows how to wrap an OpenClaw agent so it runs inside TraceCore's
deterministic episode harness, and how to map OpenClaw concepts to the
`reset/observe/act` contract.

## 1. What TraceCore expects

TraceCore instantiates your agent class once per episode and calls three methods:

| Method | When called | Purpose |
|---|---|---|
| `reset(task_spec)` | Once, before the episode starts | Initialise state from the task definition |
| `observe(observation)` | Before every step | Receive the latest environment state |
| `act() → dict` | After every `observe` | Return the next action |

The class can be named anything; the harness discovers it by scanning the module
for a class that implements all three methods. See `docs/agent_interface.md` for
the full contract and action schema.

## 2. How OpenClaw's agent loop maps to TraceCore

OpenClaw runs an LLM-driven loop internally (`agentCommand` →
`runEmbeddedPiAgent` → `pi-agent-core`). Full details: [Agent Loop](https://docs.openclaw.ai/concepts/agent-loop) · [Agent Runtime](https://docs.openclaw.ai/concepts/agent) · [Configuration Reference](https://docs.openclaw.ai/gateway/configuration-reference).

It streams three event types:

- `lifecycle` — start / end / error signals
- `assistant` — streamed LLM deltas
- `tool` — tool start / update / end events

TraceCore's harness is synchronous and step-based, so the adapter must translate
between the two models. The key insight: **one `act()` call = one tool call
decision**. Your adapter drives OpenClaw's tool selection logic and returns a
single action dict per step.

## 3. Adapter pattern

### 3a. Stateless rule-based adapter (simplest)

If you have a policy function that maps observations to tool calls, wrap it
directly — no OpenClaw runtime needed:

```python
from __future__ import annotations


class OpenClawAdapter:
    """Wraps a rule-based OpenClaw-style policy as a TraceCore agent."""

    def reset(self, task_spec: dict) -> N

*[truncated — see source for full prompt]*