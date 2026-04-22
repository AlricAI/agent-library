# Token Streaming

> How koan streams LLM token deltas from subagent processes to the browser in
realtime.

> Parent doc: [architecture.md](./architecture.md)

---

## Ove

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Token Streaming

How koan streams LLM token deltas from subagent processes to the browser in
realtime.

> Parent doc: [architecture.md](./architecture.md)

---

## Overview

Koan receives incremental token output from subagent CLI processes by parsing
their stdout line-by-line via `runner.parse_stream_event(line)` in
`koan/subagent.py`. The runner normalizes provider-specific formats into
`StreamEvent` objects. Token deltas flow to connected browsers via SSE through
the projection system.

**Design invariant:** Token streaming flows through runner stdout parsing, then
through `ProjectionStore.push_event("stream_delta", ...)`. See the SSE Path
section for details.

---

## Runner Streaming Differences

Each runner implementation parses its CLI's stdout format differently:

| Runner                                | Stdout format                               | Streaming behavior                             | Source                                              |
| ------------------------------------- | ------------------------------------------- | ---------------------------------------------- | --------------------------------------------------- |
| **Claude** (`koan/runners/claude.py`) | Stream JSON (`--output-format stream-json`) | Incremental token deltas                       | `text_delta` events in JSONL stream                 |
| **Gemini** (`koan/runners/gemini.py`) | Provider-specific JSON                      | Incremental token deltas                       | Parsed from Gemini CLI output                       |
| **Codex** (`koan/runners/codex.py`)   | Turn-level completion events                | No incremental deltas; "thinking..." indicator | Codex emits completed turns, not token-level events |

All runners implement `parse_stream_event(line) -> StreamEvent | None`. The
method returns a `StreamEvent` with a `delta` string for display, or `None` to
skip the line. The caller (`spawn_subagent()` in `koan/subagent.py`) handles
all events uniformly.

---


*[truncated — see source for full prompt]*