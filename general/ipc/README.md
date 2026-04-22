# Ipc

> HTTP MCP-based communication between the driver and subagent processes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Inter-Process Communication

HTTP MCP-based communication between the driver and subagent processes.

> Parent doc: [architecture.md](./architecture.md)
>
> The MCP endpoint at `http://localhost:{port}/mcp?agent_id={id}` is the sole
> communication channel between parent and child. See
> [architecture.md -- Directory-as-contract](./architecture.md#6-directory-as-contract).

---

## Overview

Subagent CLI processes (`claude`, `codex`, `gemini`) communicate with the
driver via HTTP MCP tool calls. The driver runs a single Starlette HTTP server
that handles both the web dashboard and the MCP tool endpoint. When a tool call
arrives, the server looks up the agent's state by `agent_id` in an in-process
registry and handles the call directly.

Three interactions involve blocking -- the HTTP request is held open while the
driver awaits an external response:

| Mechanism               | What blocks                        | Who responds                   |
| ----------------------- | ---------------------------------- | ------------------------------ |
| `koan_ask_question`     | User input needed                  | User via web UI                |
| `koan_request_scouts`   | Scout subagents running            | Driver (after scouts complete) |
| `koan_yield`            | Phase complete, awaiting direction | User via `POST /api/chat`      |

User-facing tool calls (`koan_ask_question`) go through the `PendingInteraction`
queue on `AppState`. The MCP handler creates an `asyncio.Future`, stores it in
`AgentState.pending_tool`, enqueues a `PendingInteraction` on `AppState`, and
awaits the Future. The HTTP connection stays open until the Future resolves.

`koan_request_scouts` is handled entirely inline: the handler spawns scouts via
`asyncio.gather` of `spawn_subagent` calls (bounded by a semaphore), collects
their results, and returns directly. No `PendingInteraction` is created; the
HTTP connection is held open only by the `await asyncio.gather(...)` call.

`koan_request_exe

*[truncated — see source for full prompt]*