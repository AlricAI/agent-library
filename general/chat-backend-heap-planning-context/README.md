# Chat Backend Heap Planning Context

> This document describes how the chat backend works when **heap mode** is enabled: the planner, the specialist heap, context passed to the planner and 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Chat backend: heap, planning, and context

This document describes how the chat backend works when **heap mode** is enabled: the planner, the specialist heap, context passed to the planner and specialists, and how the message queue interacts with them. It is the single place to look for “how does the backend decide which specialist runs?” and “why didn’t the planner see the previous message?”.

## Overview

When heap mode is on, each user message is processed in a pipeline:

1. **Rephrase** (optional) — User message may be rephrased or classified.
2. **Planning** — One LLM call (the “planner”) receives the user message and optional recent conversation; it outputs a structured **plan**: which specialists to run (`priorityOrder`), a short task description (`refinedTask`), extracted values like URLs/IDs (`extractedContext`), and optional per-specialist instructions.
3. **Heap execution** — The heap runs specialists in the order given by the plan. Each specialist gets the refined task plus any plan instructions and extracted context. Specialists have limited tools (e.g. only `agent` can create agents).
4. **Response** — The last specialist’s summary (and any tool results like `ask_user`) is returned. If the turn ends with `ask_user`, the plan is stored as a **pending plan** for the next turn (continuation).

When heap mode is off, a single assistant handles the message with full history and tools (no planner, no heap).

## Heap

- **What it is:** A **specialist registry** of top-level ids (e.g. `general`, `workflow`, `agent`, `improve_run`, `improve_heap`, `improve_agents_workflows`). Each specialist has a description and a set of tool names (or option groups for improvers). Some entries are “delegators” (they have subspecialists); the rest are “leaves” that actually run with their tools.
- **How routing works:** The planner outputs `priorityOrder` (e.g. `["agent", "workflow"]` or `[{ "parallel": ["agent", "workflow"] }]`). The chat route may **expand to leaves** (rep

*[truncated — see source for full prompt]*