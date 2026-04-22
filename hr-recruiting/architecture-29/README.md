# Architecture

> Koan coordinates coding task planning and execution through a single long-lived
orchestrator LLM process that runs the entire workflow in one continuo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Koan Architecture

Koan coordinates coding task planning and execution through a single long-lived
orchestrator LLM process that runs the entire workflow in one continuous session. This document captures the design invariants,
principles, and pitfalls that govern the codebase.

**Spoke documents** cover subsystems in depth:

- [Subagents](./subagents.md) -- spawn lifecycle, boot protocol, step-first
  workflow, phase dispatch, permissions, model tiers
- [IPC](./ipc.md) -- HTTP MCP inter-process communication, blocking tool calls,
  scout spawning, koan_yield blocking, chat message delivery
- [Token Streaming](./token-streaming.md) -- runner stdout parsing, SSE delta path
- [State & Driver](./state.md) -- the driver/LLM boundary, JSON vs markdown
  ownership, run state, orchestrator state
- [Projections](./projections.md) -- versioned event log, pure fold, JSON Patch
  protocol, projection model, camelCase wire format
- [Intake Loop](./intake-loop.md) -- two-step intake design, prompt engineering principles
- [Memory System](./memory-system.md) -- project memory, curation, and the RAG injection wired into phase transitions

---

## Core Invariants

These are load-bearing rules. Violating any one of them breaks the system in
ways that are difficult to diagnose.

### 1. File boundary

LLMs write **markdown files only**. The driver maintains **JSON state files**
internally -- no LLM ever reads or writes a `.json` file.

Tool code bridges both worlds: orchestrator tools write JSON state (for the
driver) and templated `status.md` (for LLMs). The driver reads JSON and exit
codes; it never parses markdown.

```
Orchestrator calls koan_complete_story(story_id)
  -> tool code writes state.json + status.md
  -> driver reads state.json to route next action
  -> LLM reads status.md if it needs to reference the decision
```

**Why:** If an LLM writes JSON, schema drift and parse errors become runtime
failures in the deterministic driver. Markdown is forgiving; JSON is not.

###

*[truncated — see source for full prompt]*