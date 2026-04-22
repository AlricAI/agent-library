# README

> This directory contains **mock agents** that are spawned by UAT journeys to
exercise specific orchestration paths. They are real Claude SDK calls with

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# _mock — UAT-only mock agents

This directory contains **mock agents** that are spawned by UAT journeys to
exercise specific orchestration paths. They are real Claude SDK calls with
tightly-constrained prompts that instruct Claude to simulate a specific
unhappy path (crash, hang, slow output). They are **not production agents**
and must never be routed by a planner or executor in a real epic.

## Agents

| Name | Purpose | Target path |
|---|---|---|
| `mock-crash-fast` | Exits non-zero immediately with a fixed stderr line | crash-fast branch in `planner_loop.py` |
| `mock-hang-long` | Blocks silently; role timeout is 5 s | stall detection / `wait_for_session()` timeout path |
| `mock-slow-steady` | Emits 12 heartbeats over 60 s then exits 0 | pane-log capture truncation (FIX-004) |

## Guardrails

1. **Excluded from valid agent roster** — `get_valid_agent_types()` in
   `modules/AgenticCLI/src/agenticcli/commands/epic.py` skips any category
   directory whose name starts with `_`. This means mock agents cannot be
   assigned to a production epic phase via `agentic epic phase add --agent`.

2. **`excluded_from_roster: true`** is set in `agent-categories.yml` for the
   `_mock` category.

3. **`uat_only: true`** is set in every mock agent's `manifest.yml`.

## Determinism mechanism

Mock agents work by giving Claude a tightly-constrained process.yml prompt
that instructs it to run a single Bash command and do nothing else. The
prompts are written to be unambiguous; the LLM has no decision space. If a
mock agent ever behaves non-deterministically the UAT should be treated as
a framework bug.

## UAT routing workaround

Since `agentic epic phase add --agent mock-*` is rejected by the production
roster validation, UAT journeys must use a two-step workaround:

```bash
# Step 1: add phase with any valid agent
agentic epic phase add --epic <folder> --id P2 --name Crash --agent build-python

# Step 2: override the agent field directly
agentic epic phase update Crash --epic

*[truncated — see source for full prompt]*