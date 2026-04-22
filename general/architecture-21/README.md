# Architecture

> For a **comparison of agent architectures** (Level 1–4: ReAct + tools, multi-agent static/dynamic, recursive/self-building) and where Agentron sits—**

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agentron Architecture

For a **comparison of agent architectures** (Level 1–4: ReAct + tools, multi-agent static/dynamic, recursive/self-building) and where Agentron sits—**Level 1** chat/RAG, **Level 2** workflows, **Level 4** heap—see the published docs: [Agent architectures (comparison)](https://docs.agentron.rocks/concepts/agent-architectures).

This repo provides a standalone, local-first Studio application:

- Electron wrapper with a Next.js UI.
- Local agent runtime and SQLite storage.
- Optional connection to remote Agentron Server instances.

**Desktop installer (future):** The goal is for the desktop app to work **independently** after install—no separate Node/npm or “run the UI” step. See [desktop-standalone.md](desktop-standalone.md) for the design and implementation checklist.

## Boundaries

- **Studio owns:** UI, local runtime, local data, local LLM installation flow, and (when deployed) can expose its own MCP server for other programs to connect to.
- **Separate Server** is only needed if you want multi-tenant hosting, independent scaling of the backend, or strict separation between “Studio frontend” and “orchestration backend.”

## Deployment: Single unit vs separate Server

You do **not** have to separate Server from Studio for typical deployments.

- **Single deployment (recommended for most cases):** Run Studio as one unit (e.g. Docker on a server or Kubernetes). Expose:
  - The Studio app port (e.g. 3000) for the UI and API.
  - The MCP endpoint (same app or dedicated port, depending on how you mount the MCP server) so other programs (IDEs, agents, CLI tools) can connect to the MCP server.
- **Opening ports:** In Docker or Kubernetes, open the appropriate ports so external clients can reach the app and the MCP server. No separate “Server” process is required for MCP access.
- **Separate Server:** Consider a dedicated Server component only if you need multiple Studios sharing one backend, multi-tenant isolation, or to scale the orchestration la

*[truncated — see source for full prompt]*