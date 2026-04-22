# CLI WIREFRAME

> This document prevents “architecture freestyling” by providing a single authoritative map:

- CLI commands (Typer)
- The core functions they call
- Th

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CodeFRAME v2 — Command Tree + Module Mapping (Cheat Sheet)

This document prevents “architecture freestyling” by providing a single authoritative map:

- CLI commands (Typer)
- The core functions they call
- The state they read/write
- The events they emit
- The adapters they may use

**Rule:** Implement commands exactly as mapped here unless `docs/GOLDEN_PATH.md` changes.

---

## Target module layout (within existing repo structure)

Repository currently uses a top-level `codeframe/` Python package and `web-ui/` at top level.

Add these subpackages under `codeframe/`:

- `codeframe/cli/`
  - `app.py` (Typer root)
  - `commands/` (subcommands grouped by domain)
- `codeframe/core/`
  - `models.py` (Pydantic/dataclasses for domain objects)
  - `state_machine.py` (authoritative transitions)
  - `events.py` (event log interface + event types)
  - `workspace.py` (workspace registration + config)
  - `config.py` (environment configuration: package manager, test framework, lint tools)
  - `prd.py` (PRD store + AI-driven generation)
  - `tasks.py` (task generation + CRUD with dependencies)
  - `blockers.py` (blocker store + AI-powered resolution)
  - `runtime.py` (single-task orchestrator/worker loop)
  - `conductor.py` (batch orchestration, multi-task execution)
  - `dependency_analyzer.py` (LLM-based dependency inference)
  - `checkpoints.py` (snapshot + restore with git refs)
  - `gates.py` (enhanced review/test runners)
  - `git_integration.py` (Git workflow and PR management)
- `codeframe/adapters/` (optional but recommended)
  - `llm/` (provider-specific clients)
  - `git/` (branch/worktree/patch utilities + PR operations)
  - `fs/` (file operations)
  - `persistence/` (SQLite/filesystem implementations)
- `codeframe/server/` (FastAPI wrapper; optional during Golden Path)
  - `app.py` (FastAPI app)
  - `routes/` (thin wrappers over core)

Legacy quarantine:
- Move `web-ui/` -> `legacy/web-ui/` (or `legacy/` equivalent)

---

## Shared concepts (authoritative)

### 

*[truncated — see source for full prompt]*