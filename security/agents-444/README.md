# AGENTS

> ## Overview

Diffray agents are defined using simple Markdown files. Each agent is a specialist with a focused responsibility - a security agent looks

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Configuration with Markdown

## Overview

Diffray agents are defined using simple Markdown files. Each agent is a specialist with a focused responsibility - a security agent looks for vulnerabilities, a bug hunter searches for logic errors.

## File Format

Each agent is defined in a `.md` file with YAML frontmatter:

```markdown
---
name: bug-hunter
description: Detects bugs, logic errors and runtime issues
enabled: true
executor: claude-cli
---

You are a bug detection specialist focused on identifying logic errors.

### Focus Areas
- Null/undefined safety
- Logic errors and incorrect conditionals
- Edge cases and boundary conditions
```

**That's it!** The body after frontmatter becomes the agent's system prompt.

## Field Reference

### Required Fields

| Field | Description |
|-------|-------------|
| `name` | Unique identifier (lowercase with dashes: `bug-hunter`) |
| `description` | Short description of what the agent does |
| `executor` | Which executor runs this agent (`claude-cli`, `codex-cli`, `cursor-agent-cli`, `opencode-cli`, `cerebras-api`) |

### Optional Fields

| Field | Default | Description |
|-------|---------|-------------|
| `enabled` | `true` | Whether the agent is active |
| `order` | `0` | Execution order (lower runs first) |

## File Locations

Agents are loaded from three locations (in priority order):

1. **User agents**: `~/.diffray/agents/*.md`
2. **Project agents**: `.diffray/agents/*.md`
3. **Built-in agents**: `src/defaults/agents/*.md`

Higher priority sources override lower ones with the same name.

## Creating Custom Agents

### 1. Create the file

```bash
# User-level agent (applies to all projects)
mkdir -p ~/.diffray/agents
touch ~/.diffray/agents/my-agent.md

# Or project-level agent
mkdir -p .diffray/agents
touch .diffray/agents/my-agent.md
```

### 2. Add frontmatter and prompt

```markdown
---
name: typescript-checker
description: Analyzes TypeScript code for type safety issues
enabled: true
executor: claude-cli
--

*[truncated — see source for full prompt]*