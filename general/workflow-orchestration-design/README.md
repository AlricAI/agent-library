# Workflow Orchestration Design

> Status: working platform doctrine for the workflow-planning layer.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Workflow Orchestration Design

Status: working platform doctrine for the workflow-planning layer. Implement against this now, but treat the exact workflow schema as provisional until more than one family has validated it.

## Purpose

This doc defines the workflow-planning layer that sits between the scheduler, model-family adapters, and host adapters.

`MLXR` now treats shared workflow planning as part of the core runtime, not as incidental glue inside one family or one host.

The immediate pressure came from `LTX-2.3 Fast`, but the point of the layer is broader:

- keep workflow intent and family-dispatched planning in one place
- let families declare truthful workflows without becoming mini-schedulers
- keep hosts thin even when tasks are multi-stage and long-running

## Mental Model

```text
Host request
  -> control plane resolves source, artifact, and capability
  -> core workflow-planning layer selects a workflow template
  -> current runtime converts that plan into the existing job lifecycle
  -> worker runs family-owned stage implementations
  -> scheduler and job system record state, telemetry, artifacts, and failures
  -> host consumes job events and output handles
```

The current workflow-planning layer is where `MLXR` decides what family/task/profile path to take and what the host is allowed to claim about the selected path. Full stage-graph interpretation, reservation ownership, and lifecycle control are still the next tranche.

## Why This Is Core MLXR

Without a core workflow-planning layer, the same mistakes repeat in different forms:

- hosts start owning stage order, warm-state assumptions, and failure handling
- families hide reusable lifecycle logic inside private adapter code
- scheduler decisions drift away from the actual execution graph
- job progress becomes a UI story instead of a runtime truth

The workflow-planning layer exists to stop that drift.

It is the runtime-owned planning bridge between:

- scheduler truth
- family-specific e

*[truncated — see source for full prompt]*