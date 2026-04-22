# Mcp Compatibility

> > **Decision (2026-03-14):** MCP compatibility is implemented as a purely additive layer.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCP Compatibility

> **Decision (2026-03-14):** MCP compatibility is implemented as a purely additive layer.
> No existing files were modified. All MCP files are optional alongside the existing skill structure.

## When MCP is and isn't needed

**Coding agents with bash access** (Antigravity, Claude Code, Kiro, Cursor, OpenCode, Copilot) already have full access to everything — agent teams, sub-agents, skills, memory — because they run bash commands directly and read their instruction file (all symlinked to `AGENTS.md`). MCP adds nothing for them.

**MCP is only needed for pure chat interfaces** with no bash execution: Claude Desktop, or any client that speaks MCP but can't run terminal commands. These clients can't call `dispatch_agent_team.py` themselves, so MCP gives them a limited window into the memory and coordination layer.

## What MCP exposes

The AGI framework exposes its memory and cross-agent coordination layer as [MCP (Model Context Protocol)](https://modelcontextprotocol.io) servers for chat-interface clients.

Two servers are provided:

| Server | File | Tools | Use when |
|---|---|---|---|
| `agi-framework` | `execution/mcp_server.py` | 16 | Daily use — memory + cross-agent + GitHub PR + health |
| `qdrant-memory` | `skills/qdrant-memory/mcp_server.py` | 6 | Direct Qdrant access (low-level ops) |

---

## Quick Setup

Add to your MCP client config (Claude Desktop: `~/.claude/claude_desktop_config.json`, Antigravity: equivalent config):

```json
{
  "mcpServers": {
    "agi-framework": {
      "command": "python3",
      "args": ["/absolute/path/to/execution/mcp_server.py"],
      "env": {
        "QDRANT_URL": "http://localhost:6333",
        "EMBEDDING_PROVIDER": "ollama",
        "OLLAMA_URL": "http://localhost:11434"
      }
    }
  }
}
```

> **Prerequisites:** Qdrant running on port 6333, Ollama running with `nomic-embed-text` pulled.
> Use `python3 execution/session_boot.py --auto-fix` to verify and repair.

---

## `agi-framework` — Executio

*[truncated — see source for full prompt]*