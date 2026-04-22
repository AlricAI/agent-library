# AGENT MEMORY QUICKSTART

> This quickstart covers the memory surfaces verified in this checkout today:

- the top-level `amplihack memory tree` graph view
- the agent-local `amp

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Memory Quickstart

This quickstart covers the memory surfaces verified in this checkout today:

- the top-level `amplihack memory tree` graph view
- the agent-local `amplihack memory export` / `amplihack memory import` transfer commands
- generated goal-agent packages created with `amplihack new --enable-memory`

## 1. Inspect the Top-Level CLI Memory Graph

The top-level graph view uses `MemoryDatabase`, a SQLite store at `~/.amplihack/memory.db` by default.

```bash
amplihack memory tree
```

Useful variants:

```bash
amplihack memory tree --depth 2
amplihack memory tree --session test_session_01
amplihack memory tree --type learning
```

`memory tree --type` currently accepts the legacy compatibility names:

- `conversation`
- `decision`
- `pattern`
- `context`
- `learning`
- `artifact`

## 2. Generate a Memory-Enabled Goal Agent

```bash
printf '%s\n' \
  'Build an agent that investigates deployment failures, remembers repeated causes, and suggests the next debugging step.' \
  > goal.md

amplihack new \
  --file goal.md \
  --name incident-memory-agent \
  --enable-memory \
  --sdk copilot
```

That creates a package under `./goal_agents/incident-memory-agent/`.

## 3. Install and Run the Generated Agent

```bash
cd goal_agents/incident-memory-agent
python -m pip install -r requirements.txt
python main.py
```

When `--enable-memory` is set, the generated package includes:

- `memory_config.yaml`
- a local `./memory/` directory
- helper functions in `main.py` such as `store_success()`, `store_failure()`, and `recall_relevant()`
- `amplihack-memory-lib` in `requirements.txt`

## 4. Export or Import an Agent-Local Memory Store

Use the transfer commands when you want to move an agent's hierarchical memory between environments.

```bash
amplihack memory export --agent incident-memory-agent --output ./incident-memory.json
amplihack memory import --agent incident-memory-agent --input ./incident-memory.json --merge
```

For raw Kuzu store replacement instead o

*[truncated — see source for full prompt]*