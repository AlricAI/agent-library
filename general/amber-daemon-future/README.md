# AMBER DAEMON FUTURE

> *Date: 2026-02-02*

## Current State

Amber has her own daemon (`amber-daemon/`) that provides:

- **Agent loop** — `runAgentLoop()` in `amber.js`
- *

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Amber Daemon: Architecture & Future

*Date: 2026-02-02*

## Current State

Amber has her own daemon (`amber-daemon/`) that provides:

- **Agent loop** — `runAgentLoop()` in `amber.js`
- **Multi-surface routing** — TUI + Discord via Unix socket
- **Memory system** — `~/.amber/memory/` (just built)
- **Context compaction** — Auto-flush to daily logs before trimming
- **Custom tools** — discord, supabase, git, memory

### Directory Structure

```
~/.amber/
├── memory/
│   ├── PERSONA.md          # Identity (stable)
│   ├── MEMORY.md           # Long-term facts
│   └── YYYY-MM-DD.md       # Daily logs (append-only)
├── conversation.json       # Sliding window (50-80 messages)
├── daemon-state.json       # Last seen timestamps
└── amber.sock              # Unix socket for TUI/Discord
```

### Tools Available

| Tool | Purpose |
|------|---------|
| `read_file` / `write_file` / `list_directory` | File operations |
| `run_command` | Shell commands |
| `web_search` | DuckDuckGo search |
| `discord_read` / `discord_post` | Discord #agent-lounge |
| `supabase_query` | Query amber_state table (SELECT only) |
| `git_log` | Recent repo activity |
| `memory_append` | Save notes to daily log |
| `memory_search` | Search memory files |

---

## The OpenClaw Discovery

We have another agent system called **OpenClaw** that:

1. Uses Claude Code directly (not a DIY recreation)
2. Gets the full Claude Code system prompt + tools upstream
3. Layers persona on top (SOUL.md, USER.md, MEMORY.md)
4. Handles routing, sessions, compaction, memory

### OpenClaw's Core Loop

```
User message → OpenClaw gateway → Claude API (with Claude Code prompt + tools)
                                          ↓
                                Model decides: reply or tool call?
                                          ↓
                               ┌──────────┴──────────┐
                               ↓                     ↓
                            [reply]             [tool call]
                  

*[truncated — see source for full prompt]*