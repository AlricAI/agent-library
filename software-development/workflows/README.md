# Workflows

> Tandem workflows provide a declarative layer for extending agent and automation behavior without changing core engine code.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Workflows

Tandem workflows provide a declarative layer for extending agent and automation behavior without changing core engine code.

The v1 implementation adds:

- workflow definitions loaded from YAML
- event-driven hook bindings
- pack and workspace workflow discovery
- workflow run persistence
- workflow simulation and execution APIs

## Architecture Overview

The workflow layer is engine-owned.

- `tandem-workflows` defines schemas, loading, merge rules, and validation.
- `tandem-server` owns runtime execution, event dispatch, persistence, and HTTP APIs.
- the existing Tandem event bus remains the source of truth for triggers and workflow lifecycle events.

Workflow sources are merged in this order:

1. built-in workflow directories
2. installed packs
3. workspace-local `.tandem`

Later sources override earlier workflow definitions with the same `workflow_id`. Hook enablement can be overridden at runtime without editing source files.

## Workflow Definition

Workflow files live under a `workflows/` directory and use YAML.

Example:

```yaml
workflow:
  id: build_feature
  name: Build Feature
  description: Standard feature delivery pipeline
  steps:
    - planner
    - action: task_generator
      with:
        max_tasks: 5
    - executor
    - verifier

  hooks:
    task_created:
      - kanban.update
    task_completed:
      - slack.notify
```

Each step is normalized into a `WorkflowStepSpec`:

- `step_id`
- `action`
- optional `with` payload

Supported action prefixes in v1:

- `capability:<id>`
- `tool:<id>`
- `agent:<id>`
- `workflow:<id>`
- `event:<type>`
- `resource:put:<key>`
- `resource:patch:<key>`
- `resource:delete:<key>`

If no prefix is supplied, Tandem treats the action as `capability:<id>`.

## Event System

The engine maps runtime events to canonical workflow lifecycle names.

Standard names:

- `workflow_started`
- `task_created`
- `task_started`
- `task_completed`
- `task_failed`
- `workflow_completed`

Current built-in mappings include

*[truncated — see source for full prompt]*