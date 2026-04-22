# FLOOP USAGE

> > How to use floop for persistent AI agent memory — via MCP (recommended) or CLI.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Floop Usage Guide

> How to use floop for persistent AI agent memory — via MCP (recommended) or CLI.

## Overview

floop captures corrections, extracts reusable behaviors, and activates them in context. New to floop? Start with the [5-minute walkthrough](WALKTHROUGH.md) to see the full learning loop in action.

It works via two interfaces:
- **MCP tools** (recommended) — Direct integration with AI tools like Claude Code, Cursor, etc.
- **CLI commands** — Full control from the terminal, useful for scripting and manual management

## MCP Tools (Recommended)

When configured as an MCP server, floop exposes these tools to your AI agent:

| Tool | Purpose |
|------|---------|
| `floop_active` | Get behaviors relevant to current context (file, task) |
| `floop_learn` | Capture a correction or insight |
| `floop_list` | List all stored behaviors |
| `floop_connect` | Create edges between behaviors |
| `floop_feedback` | Provide session feedback on a behavior (confirmed/overridden) |
| `floop_deduplicate` | Find and merge duplicate behaviors |
| `floop_graph` | Render behavior graph (DOT, JSON, or HTML) |
| `floop_validate` | Check graph consistency |
| `floop_backup` | Export graph state to backup file |
| `floop_restore` | Import graph state from backup |

### MCP Setup

Add floop as an MCP server in your AI tool's config. Example for Claude Code (`~/.claude/settings.json`):

```json
{
  "mcpServers": {
    "floop": {
      "command": "floop",
      "args": ["mcp-server"]
    }
  }
}
```

See [docs/integrations/](integrations/) for more tools.

### MCP Resources

The MCP server also exposes resources that clients can subscribe to:

| URI | Description |
|-----|-------------|
| `floop://behaviors/active` | Active behaviors for current context (auto-loaded, 2000-token budget) |
| `floop://behaviors/expand/{id}` | Full details for a specific behavior (resource template) |

### MCP Workflow

```
# Agent automatically gets active behaviors via floop_active at session start
#

*[truncated — see source for full prompt]*