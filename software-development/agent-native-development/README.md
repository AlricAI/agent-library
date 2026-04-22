# Agent Native Development

> Status: current operating model for implementation work in `MLXR`.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent-Native Development

Status: current operating model for implementation work in `MLXR`.

## Purpose

This doc explains how the repo is meant to run day to day when Codex is the primary execution engine.

The human is expected to:

- set direction
- define success
- review outcomes
- make judgment calls when tradeoffs are real

Codex is expected to:

- inspect context
- implement changes
- run the harness
- inspect logs when runtime behavior changes
- update docs when repo truth changes
- commit only from green

Fresh sessions should bootstrap from repo files alone. The repo should not depend on a custom kickoff prompt to establish the operating model.

## Startup Order

At session start:

1. read `AGENTS.md`
2. read `MEMORY.md`
3. read the declared core docs
4. inspect `git status`
5. inspect recent commits
6. inspect the current implementation and harness state

This startup order is part of the repo contract, not optional ceremony.

## Normal Working Sequence

1. Read the repo doctrine and relevant platform docs.
2. Inspect the local implementation before making assumptions.
3. If the user has not tightly scoped the next task, derive the next step from repo state.
4. Implement the smallest complete change that satisfies the task.
5. Run the local harness.
6. If the task touches runtime behavior, inspect logs as part of validation.
7. If the task changes repo-level truth, update docs in the same pass.
8. Do a fresh-eyes review pass on the diff before commit.
9. Commit once the repo is green.

## How To Decide What To Do Next

When the user has not provided a narrowly scoped next task, derive the next step from repo evidence.

Priority order:

1. broken startup or development loop
2. broken validation, logging, or observability
3. docs-code mismatches or architecture contract drift
4. the highest-leverage incomplete implementation step implied by current docs and recent commits

Do not stall waiting for more direction when the next step is discoverable from t

*[truncated — see source for full prompt]*