# Autonomous Agentic Research Workflow Roadmap

> This document defines a reusable, file-based workflow for running multiple AI coding/research agents in parallel on research projects (empirical, mode

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Autonomous Agentic Research Workflow (Reusable Architecture + Roadmap)

This document defines a reusable, file-based workflow for running multiple AI coding/research agents in parallel on research projects (empirical, modeling, or hybrid) with minimal conflict and minimal human babysitting.

It is designed to work with **subscription CLIs/IDEs** (e.g., Claude Code, Codex CLI) and does **not** assume API-based agent frameworks.

For the concrete “how to run this swarm” commands (worktrees, headless runs, fresh starts), see `docs/runbook_swarm.md`.

---

## 1) Design goals

**Goal:** A “research team in a repo” where agents can work in parallel, produce auditable outputs, and keep going unattended—while avoiding contradictions and clobbering.

**Non-goals (at first):**
- Not building a complex “agents talk to each other” system.
- Not relying on shared chat as the coordination substrate.
- Not attempting fully automated merges without quality gates.

Terminology: “Contracts & locks” refers to canonical specs. For empirical projects, the protocol lock is implemented as `docs/protocol.md` plus schema contracts under `contracts/`.

---

## 1.5) Research modes (required)

Every project must declare a mode:

- **Empirical**: data collection + cleaning + validation + estimation
- **Modeling**: formal model/spec + solution method + experiments/simulation + validation
- **Hybrid**: both (empirical informs model; model generates counterfactuals)

Mode determines which repo modules and contracts are mandatory.

---

## 2) The core architecture (Planner → Workers → Judge)

### Roles

- **Planner (human or agent)**
  - Reads the research plan + current repo state.
  - Decomposes work into small tasks with clear I/O contracts.
  - Assigns tasks to workstreams and defines ownership boundaries.

- **Workers (multiple agents)**
  - Each worker executes *one task at a time* in an isolated workspace (branch/worktree).
  - Writes outputs to the agreed paths and updates only the task’s

*[truncated — see source for full prompt]*