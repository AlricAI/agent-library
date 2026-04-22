# Runbook Swarm Automation

> This runbook is the **human-facing** step-by-step guide for starting and operating the automated research swarm in this repo.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Swarm Automation Runbook (press‑go guide)

This runbook is the **human-facing** step-by-step guide for starting and operating the automated research swarm in this repo.

It is designed for: **“I’m in a devcontainer / VM, I want to kickstart the swarm, and I don’t want surprises.”**

---

## What this automation actually does (read this once)

### Control plane vs automation plane

- **Control plane (Planner hygiene):**
  - Task files live under `.orchestrator/`.
  - Tasks have a `State:` field inside the file:
    `backlog | active | blocked | ready_for_review | done`.
  - **Only the Planner** is supposed to move task files between lifecycle folders.
  - The tool for that is: `python scripts/sweep_tasks.py` (also `make sweep`).

- **Automation plane (Worker + Judge):**
  - The supervisor is `python scripts/swarm.py`.
  - It selects “ready” tasks in `.orchestrator/backlog/` whose `State: backlog` **and** whose dependencies are already `State: done`.
  - For each selected task it:
    1) creates a **git worktree** in a sibling directory (default: `../wt-T###`)
    2) runs **Codex CLI** as Worker to implement the task
    3) runs **gates** (usually `make gate`, sometimes `make test`) as Judge
    4) enforces **path ownership** (only allowed_paths, no forbidden `.orchestrator/` edits except the task file + handoff notes)
    5) updates the task file’s `State:` and appends a note under `## Notes / Decisions`
    6) commits + pushes the branch
    7) optionally opens a PR and optionally requests auto-merge

### Important governance design (Option A — this repo’s rule)

This repo intentionally separates:
- **state updates** (automation does this),
from
- **moving task files between folders** (Planner does this).

Concretely:
- `scripts/swarm.py` updates the task file’s `State:` and notes, but **does not** `git mv` tasks between folders.
- `scripts/sweep_tasks.py` reads each task’s `State:` and **does** `git mv` the file into the matching folder.

Dependencies are satisfi

*[truncated — see source for full prompt]*