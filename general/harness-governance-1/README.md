# Harness Governance

> This document turns long-running agent guidance into repo-local operating rules.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Harness & Governance

This document turns long-running agent guidance into repo-local operating rules.
The goal is simple: a fresh agent or reviewer should be able to understand the
current state, the authority boundaries, and the proof of work from repository
artifacts alone.

## Operating Model

- Humans steer. Agents execute.
- The repo is durable memory. Plans, runbooks, status notes, screenshots,
  result JSON, and git history must be enough for a fresh context to resume.
- Multi-step work is checkpointed. Each milestone needs clear constraints,
  validation commands, and a stop-and-fix rule before the next milestone.
- Prefer specialized surfaces over one giant agent. CLI, web, TUI, workers,
  and draft review share the same backend contract but keep distinct runtime
  responsibilities.
- Hidden chat state is not a source of truth. If it matters later, write it
  into the repo or the per-run artifacts.

## Durable Artifact Stack

The default artifact stack for long-running work in this repo is:

1. `AGENTS.md`, `agent_preferences.md`, and `docs/core-beliefs.md`
   for standing behavior and invariants.
2. `docs/exec-plans/active/*.md` for the current multi-step task.
3. `docs/operational-rules.md`, `docs/backlog-sweep.md`, and
   `docs/runbooks/*` for surface-specific runbooks.
4. Per-job proof in `output/<company>/<role>/submit/` and related structured
   runtime artifacts.
5. Git history for change lineage and rollback.

If a task spans multiple sessions, approvals, or handoffs, the active plan must
stay current enough that another agent can resume from the repo alone.

## Shared Settings And User Context

All operator surfaces must resolve the same user-owned materials and
credentials through `scripts/app_paths.py` and `scripts/settings_store.py`.
No surface may introduce a shadow copy of user context or a separate settings
schema without updating this contract.

Canonical user context files:

- `master_resume.md`
- `work_stories.md`
- `candidate_context.m

*[truncated — see source for full prompt]*