# Per Phase Model Selection Plan

> ### Decisions

- Koan adds a new root command parser via `/koan`, with `config` as the first subcommand.
- `/koan config` opens a settings-style menu 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
## Context

### Decisions

- Koan adds a new root command parser via `/koan`, with `config` as the first subcommand.
- `/koan config` opens a settings-style menu with one section now: `Model selection`.
- `Model selection` uses a 5x4 matrix:
  - Rows: `plan-design`, `plan-code`, `plan-docs`, `exec-code`, `exec-docs`
  - Columns: `exec-debut`, `exec-fix`, `qr-decompose`, `qr-verify`
- Each matrix cell maps to one canonical key in the `phase-model` namespace (20 total keys).
- Cell picker uses an inline anchored selector and sources models from pi's model registry (`ctx.modelRegistry.getAvailable()`), matching `/model` inventory semantics.
- Quick-set controls exist at the top of model selection:
  - `Reset to active model` clears koan model overrides
  - `Set strong model` applies one chosen model to strong keys
  - `Set general-purpose model` applies one chosen model to all remaining keys
- Strong key set is fixed:
  - All `*-qr-decompose`
  - `plan-design-exec-debut`, `plan-design-exec-fix`
  - `exec-docs-exec-debut`, `exec-docs-exec-fix`
- General-purpose key set is computed as `all keys - strong keys`.
- Storage is denormalized: config persists either all 20 key/value pairs or none.
- Runtime model application happens only at subagent spawn time by passing `--model <provider/model>` when override exists.
- If koan model config is absent, all phases inherit pi's current active model by omitting `--model`.
- Quick-set writes always preserve all-or-none persistence: when no saved config exists, untouched keys are initialized from the current active model snapshot so all 20 keys are still written.
- Naming aligns precursor terminology to `exec-debut` and removes `exec-init` equivalents in koan-facing labels.

### Rationale

- Settings-style navigation matches existing pi interaction patterns and lowers learning cost.
- Matrix layout gives complete phase visibility and keeps override auditing simple.
- Quick-set controls reduce repetitive edits and enforce consistent 

*[truncated — see source for full prompt]*