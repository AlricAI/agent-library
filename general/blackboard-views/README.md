# BLACKBOARD VIEWS

> ## Purpose

Define an implementation-ready UI plan for Blackboard visualization that is consistent with the current engine context-driving runtime.

P

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Blackboard Views Plan (Desktop Orchestrator + Command Center)

## Purpose

Define an implementation-ready UI plan for Blackboard visualization that is consistent with the current engine context-driving runtime.

Primary goals:

- keep AI execution on track with explicit state visibility
- show progress clearly (run + step + task flow)
- show why the AI made each decision (`why_next_step`)
- keep Engine as the single source of truth

## Source-of-Truth Contract

Engine owns truth. Desktop/TUI are views/controllers.

- Truth from engine:
  - `/context/runs/{run_id}` (`status`, `steps`, `why_next_step`)
  - `/context/runs/{run_id}/events` and `/events/stream` (sequenced decisions/activity)
  - `/context/runs/{run_id}/blackboard` (materialized blackboard)
  - `/context/runs/{run_id}/replay` (drift/integrity)
  - `/context/runs/{run_id}/checkpoints/latest` (resume marker)
- UI must not infer status from transcript/log text.

## Scope

In scope:

- Desktop Orchestrator page
- Desktop Command Center page
- shared `BlackboardPanel` component with `docked|expanded|fullscreen` modes

Out of scope:

- chat surfaces
- UI-editing blackboard patches
- alternate non-engine run truth

## Fit With Current Engine System

This plan is aligned to what exists today:

- Sequenced context events with `seq` and SSE stream
- `meta_next_step_selected` events with `why_next_step`
- `todo_synced` events from todo->step sync bridge
- `workspace_mismatch` reliability event
- replay endpoint returning drift flags
- checkpoint latest endpoint

Important implementation note:

- there is no dedicated blackboard patch stream endpoint in current contracts.
- live updates should be driven by `/events/stream`, then refresh blackboard materialized view (`/blackboard`) as needed.

## UX Model

### Mode 1: Docked (default)

Render lightweight overview only (no heavy graph mount):

- run status pill
- current/next step label
- `why_next_step` (1-2 line clamp)
- progress counters:
  - done/total steps
  - 

*[truncated — see source for full prompt]*