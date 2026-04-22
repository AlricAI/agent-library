# Agent Memory

> Swarms agents have a built-in persistent memory system that survives across process restarts.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Memory

Swarms agents have a built-in persistent memory system that survives across process restarts. Every agent gets its own folder on disk under the workspace directory, with a `MEMORY.md` file that records every user task and agent response. When the agent is instantiated again with the same `agent_name`, the prior memory is automatically loaded back into its working context.

This document covers the full memory stack:

- `MEMORY.md` persistent memory
- `Conversation.compact()` for collapsing history into a summary
- `ContextCompressor` for automatic compression during autonomous runs
- The archive system that preserves raw chat logs forever

## Overview

Agent memory lives at a predictable path under `$WORKSPACE_DIR`:

```
$WORKSPACE_DIR/agents/{agent_name}/
├── MEMORY.md                          # active, append-updated
└── archive/
    ├── history_2026-04-20_14-30-45.md # prior MEMORY.md before last compaction
    ├── history_2026-04-20_16-12-08.md
    └── ...
```

**Key design points**

- The folder is keyed on `agent_name` only (not `id`), so running the same agent across multiple processes resumes the same memory.
- `MEMORY.md` is append-only during normal operation. Every `conversation.add(role, content)` call writes through to disk.
- When compression fires, the current `MEMORY.md` is archived to `archive/history_<timestamp>.md` before being wiped. Raw chat logs are never destroyed.
- Only user messages, agent responses, and tool results hit `MEMORY.md`. The static `system_prompt` and `rules` are kept out of the file (they come from the `Agent` constructor on each run).

## How It Works

### 1. File creation

On first instantiation of an agent with a given `agent_name`, the Conversation creates:

```
$WORKSPACE_DIR/agents/{agent_name}/MEMORY.md
```

seeded with a small header:

```markdown
# Agent Memory

**Conversation:** QuantAgent_id_<uuid>_conversation
**Created:** 2026-04-20T18:33:12

---

## Interaction Log
```

If the file already exists,

*[truncated — see source for full prompt]*