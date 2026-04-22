# CLI REFERENCE

> Complete reference for all floop commands.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# floop CLI Reference

Complete reference for all floop commands. floop manages learned behaviors and conventions for AI coding agents -- it captures corrections, extracts reusable behaviors, and provides context-aware behavior activation for consistent agent operation.

**Version:** 0.8.0

---

## Global Flags

These flags are available on every command.

| Flag | Type | Default | Description |
|------|------|---------|-------------|
| `--json` | bool | `false` | Output as JSON (for agent consumption) |
| `--root` | string | `.` | Project root directory |
| `--version`, `-v` | bool | `false` | Print version information and exit |

---

## Core

Commands for initializing floop, capturing corrections, and managing hooks.

### init

Initialize floop with hooks and behavior learning.

```
floop init [flags]
```

Configures Claude Code hook settings to use native `floop hook` subcommands, seeds meta-behaviors, and creates the `.floop/` data directory.

**Interactive mode** (no flags): Prompts for installation scope, hooks, and token budget.
**Non-interactive mode** (any flag provided): Uses flag values with sensible defaults. Suitable for scripts and agents.

| Flag | Type | Default | Description |
|------|------|---------|-------------|
| `--global` | bool | `false` | Install hooks globally (`~/.claude/`) |
| `--project` | bool | `false` | Install hooks for this project (`.claude/`) |
| `--hooks` | string | `""` | Which hooks to enable: `all`, `injection-only` (default in non-interactive: `all`) |
| `--token-budget` | int | `2000` | Token budget for behavior injection |
| `--embeddings` | bool | `false` | Download and enable local embeddings for semantic retrieval |
| `--no-embeddings` | bool | `false` | Skip local embeddings setup |

**Examples:**

```bash
# Interactive setup
floop init

# Global install with all defaults
floop init --global

# Project-level install with all defaults
floop init --project

# Both scopes with explicit options
floop init --global --proje

*[truncated — see source for full prompt]*