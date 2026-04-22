# Assistant / Specialist Structure (Agentron)

> description: Agentron assistant specialist structure — 10-tool cap per specialist and traceable logging globs: packages/runtime/src/chat/**/*.ts, packages/ui/app/api/chat/**/*.ts alwaysApply: false

## System Prompt
---
description: Agentron assistant specialist structure — 10-tool cap per specialist and traceable logging
globs: packages/runtime/src/chat/**/*.ts, packages/ui/app/api/chat/**/*.ts
alwaysApply: false
---

# Assistant / Specialist Structure (Agentron)

When editing the **Agentron assistant agent specialist structure** (tool sets, specialist registry, router, or chat route that runs them), follow these rules.

## 1. Cap: No more than 10 tools per specialist

- **Every specialist must have at most 10 tools.** When adding or changing tools for a specialist, count the tools; if the result would exceed 10, **split the specialist** into two (or more) sub-specialists with disjoint tool sets.
- Applies to:
  - Any module that defines a **named tool set** (e.g. `AGENT_TOOLS`, `WORKFLOW_TOOLS`, or future `*_SPECIALIST_TOOLS`).
  - Any **specialist registry** or map from specialist id to tool array.
  - The combined **flat** assistant tool list is exempt (used for legacy/single-agent mode); the cap applies to **per-specialist** sets only.
- **How to enforce:** When adding a new tool to a specialist set, check `array.length` (or add a comment/code check): if adding one would make it > 10, create a new sub-specialist (e.g. split "Workflow" into "Workflow definition" and "Run control") and assign tools to the appropriate set.
- **Example:** If "Improvement" has 8 tools and you need to add 3 more, do not add all to the same set; create "Improvement jobs" (8) and "Optimization & technique" (3) and register both.

## 2. Traceable execution logging (assistant stack trace)

Add **structured logging** so execution can be traced end-to-end from the assistant stack (router → specialist → tool calls → results).

### Requirements

- **Correlation:** Use a single **trace id** (e.g. `traceId` or `requestId`) for the whole chat turn and log it on every relevant line so logs can be filtered (e.g. `grep traceId=abc logs`).
- **Router:** When the router runs, log at least: `traceId`, phase `rou

*[truncated — see source for full prompt]*