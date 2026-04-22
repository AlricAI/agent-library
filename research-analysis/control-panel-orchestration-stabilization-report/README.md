# CONTROL PANEL ORCHESTRATION STABILIZATION REPORT

> Date: March 6, 2026

## Purpose

This report summarizes the stabilization and standardization work completed on Tandem's control-panel orchestration p

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Control Panel Orchestration Stabilization Report

Date: March 6, 2026

## Purpose

This report summarizes the stabilization and standardization work completed on Tandem's control-panel orchestration path.

The target design is:

```text
Run State (source of truth)
  -> Blackboard Projection
  -> UI Panels
```

The main goal of this work was to stop treating the blackboard as the primary mutable task store and move the web control panel toward a deterministic, run-scoped, multi-run-safe orchestration model.

## Starting Problems

Before this work:

- the control panel used a mix of global server state and per-run state
- the UI rebuilt task state from multiple sources
- `blackboard.tasks` behaved like a writable task authority
- `run_state.json` and blackboard task state could diverge
- task transitions were too permissive
- the backend had duplicate context-run implementations
- event append and run mutation ordering were not consistently serialized

## What Was Accomplished

### 1. Control-panel runtime was made run-scoped

The control-panel server no longer relies primarily on one global active swarm state for all orchestration runs.

Completed changes:

- added per-run controller state in `packages/tandem-control-panel/bin/setup.js`
- updated swarm/control routes to resolve and persist state by `runId`
- fixed executor mode, verification mode, workflow id, and workspace resolution to be run-local
- reduced cross-run leakage in status, retry, continue/resume, and verification behavior

Result:

- the control panel is substantially safer for concurrent runs
- one run's executor/verification state is much less likely to bleed into another run

### 2. The web UI now prefers one canonical task model

The control panel now renders orchestration tasks through a single projection layer instead of ad hoc task normalization scattered through the page.

Completed changes:

- added `packages/tandem-control-panel/src/features/orchestrator/blackboardProjection.ts`
- updated 

*[truncated — see source for full prompt]*