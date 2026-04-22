# Subagents

> How koan spawns, manages, and terminates LLM subagent processes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Subagents

How koan spawns, manages, and terminates LLM subagent processes.

> Parent doc: [architecture.md](./architecture.md)

---

## Task Manifest

Every subagent starts as a CLI process (`claude`, `codex`, or `gemini`) with
MCP config pointing at the driver's HTTP endpoint. The driver reads `task.json`
from the subagent directory to set up the agent's state in the in-process
registry.

### `task.json` schema

The manifest is a discriminated union on the `role` field. Common fields
(`role`, `run_dir`, `mcp_url`) appear on every variant; role-specific fields
are nested naturally rather than flattened into a shared namespace.

```json
{
  "role": "intake",
  "run_dir": "/path/to/run",
  "mcp_url": "http://localhost:8420/mcp?agent_id=intake-abc123"
}
```

Role-specific fields:

| Role           | Additional fields                 |
| -------------- | --------------------------------- |
| `orchestrator` | `project_dir`, `task_description` |
| `scout`        | `question`, `investigator_role`   |
| `executor`     | `artifacts`, `instructions`       |

### Lifecycle

`task.json` is **write-once, read-once**:

1. Driver creates the subagent directory
2. Driver writes `task.json` (atomic: tmp + rename)
3. Driver assigns `agent_id`, registers agent in in-process registry
4. Driver writes MCP config and spawns the CLI process
5. Child connects to `mcp_url`, calls `koan_complete_step`
6. `task.json` is never modified after spawn

This makes every subagent directory **self-describing** and **inspectable**
after the fact. `cat task.json` shows exactly what the subagent was asked
to do.

### Why not CLI flags

The previous design passed task configuration as 9 CLI flags. Problems:

| Problem                      | Example                                                                    |
| ---------------------------- | -------------------------------------------------------------------------- |
| **Flat namespace collision** | `--koan-role` vs `--koan-scout-role` -- two u

*[truncated — see source for full prompt]*