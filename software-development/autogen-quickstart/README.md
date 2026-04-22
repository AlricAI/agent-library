# Autogen Quickstart

> This guide shows how to test an AutoGen multi-agent team inside TraceCore's
deterministic benchmark harness, using the automatic adapter generator to


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AutoGen Quickstart (TraceCore)

This guide shows how to test an AutoGen multi-agent team inside TraceCore's
deterministic benchmark harness, using the automatic adapter generator to
eliminate manual rewrites.

## 1. What TraceCore expects

TraceCore instantiates your agent class once per episode and calls three methods:

| Method | When called | Purpose |
|---|---|---|
| `reset(task_spec)` | Once, before the episode starts | Initialise state from the task definition |
| `observe(observation)` | Before every step | Receive the latest environment state |
| `act() → dict` | After every `observe` | Return the next action |

The class can be named anything; the harness discovers it by scanning the module
for a class that implements all three methods. See `docs/agent_interface.md` for
the full contract.

## 2. How AutoGen's model differs from TraceCore

AutoGen runs **conversational loops** — a team of agents chat back and forth
until a termination condition is met. The entire conversation happens in one
`team.run()` call.

TraceCore runs **step-based episodes** — the harness calls `observe → act` in a
loop, one action per step, with budget enforcement and full observability at
every step.

These are fundamentally different execution models. You can't just wrap
`team.run()` as a black box because:

- TraceCore can't see inside the conversation (no per-step trace)
- TraceCore can't enforce budgets on individual actions
- The conversational output is a final answer, not a sequence of actions

## 3. The three integration approaches

| Approach | How it works | Tradeoff |
|---|---|---|
| **Pure adapter** | Wrap `team.run()` as a black box, return final answer | Simple but loses observability and budget control |
| **Per-step LLM** | Each `act()` = one short AutoGen conversation | True adapter but fragile — LLM must produce valid action JSON every time |
| **Hybrid** (recommended) | Generic state machine handles known patterns; AutoGen team consulted for novel situations | R

*[truncated — see source for full prompt]*