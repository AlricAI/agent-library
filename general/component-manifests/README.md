# Component Manifests

> These manifests give AI agents a conservative map of the first-party components implemented in this repository.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tandem Component Manifests

These manifests give AI agents a conservative map of the first-party components implemented in this repository.

They are intended to answer:

- what Tandem is
- which top-level components this repo owns
- which runtime surfaces are present here
- which repo paths are the source of truth for each component

## Manifest Locations

- Canonical source manifests live in `manifests/components/`.
- Agent-runtime copies live in `src-tauri/resources/agent-context/component-manifests/`.
- When a manifest is updated, both locations should be updated in the same change.

## Included Components

| Component              | Kind              | Manifest                                                                         | Why it has its own manifest                                                                                           | Primary source-of-truth paths                                                                                                                    |
| ---------------------- | ----------------- | -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `tandem-engine`        | `runtime`         | [`tandem-engine.yaml`](../manifests/components/tandem-engine.yaml)               | Central runtime, API surface, orchestration, workflows, automations, memory, tools, and coordination state live here. | `engine/`, `crates/tandem-server/`, `crates/tandem-runtime/`, `crates/tandem-orchestrator/`, `crates/tandem-memory/`, `crates/tandem-workflows/` |
| `tandem-desktop`       | `desktop-client`  | [`tandem-desktop.yaml`](../manifests/components/tandem-desktop.yaml)             | The Tauri desktop application is a distinct first-party us

*[truncated — see source for full prompt]*