# State

> How the driver manages run state, routes between phases, and enforces the file
boundary invariant.

> Parent doc: [architecture.md](./architecture.md)

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# State & Driver

How the driver manages run state, routes between phases, and enforces the file
boundary invariant.

> Parent doc: [architecture.md](./architecture.md)

---

## The File Boundary in Practice

The driver writes JSON; LLMs write markdown. Tool code bridges both.

| Actor         | Reads                           | Writes                              |
| ------------- | ------------------------------- | ----------------------------------- |
| **Driver**    | `.json` state files, exit codes | `.json` state files                 |
| **LLM**       | `.md` files, codebase files     | `.md` files (output)                |
| **Tool code** | `.json` state (to validate)     | `.json` state + `.md` status (both) |

### Why the run state module must not write markdown

The run state module (`koan/run_state.py`) reads and writes JSON only.
`status.md` writes belong exclusively in orchestrator tool handlers, which
bridge the two worlds by writing JSON state (for the driver) and templated
markdown (for LLMs) in the same operation.

### Filesystem-driven story discovery

Story IDs are discovered by scanning `stories/*/story.md`, not by reading a
driver-maintained JSON list. The orchestrator (during the ticket-breakdown phase) creates `story.md` files using
the `write` tool -- it has no reason to know the JSON state format. The driver
discovers what the LLM created by scanning, then populates the JSON story list
itself.

---

## Run State

`run-state.json` in the run directory root. Tracks the current workflow phase,
the active workflow type, and the list of story IDs.

```python
# koan/run_state.py
{
    "phase": "intake",        # current phase name; valid values depend on the active workflow
    "workflow": "plan",       # workflow type selected at run start ("plan" | "milestones")
    "stories": []             # populated by driver after filesystem scan
}
```

### Plan workflow phases

| Phase | What happens |
|-------|--------------|
| `intake` | Orchestrator re

*[truncated — see source for full prompt]*