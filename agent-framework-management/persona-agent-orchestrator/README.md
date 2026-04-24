# Readme

> Persona-Based Agents — agent-native AI orchestrator for Personas. Works with Claude Code, Codex CLI, Gemini CLI, and OpenClaw.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Persona-Based Agents

<div class="page-meta" markdown>
<span class="meta-badge">:material-robot: Agent</span>
<span class="meta-badge">:material-account: Personas</span>
<span class="meta-badge">:material-github: <a href="https://github.com/alirezarezvani/claude-skills/tree/main/agents/personas/README.md">Source</a></span>
</div>


Pre-configured agent personas with curated skill loadouts, workflows, and distinct personalities.

## What's a Persona?

A **persona** is an agent definition that goes beyond "use these skills." Each persona includes:

- **🧠 Identity & Memory** — who this agent is, how they think, what they've learned
- **🎯 Core Mission** — what they optimize for, in priority order
- **🚨 Critical Rules** — hard constraints they never violate
- **📋 Capabilities** — domain expertise organized by area
- **🔄 Workflows** — step-by-step processes for common tasks
- **💭 Communication Style** — how they talk, with concrete examples
- **🎯 Success Metrics** — measurable outcomes that define "good"
- **🚀 Advanced Capabilities** — deeper expertise loaded on demand
- **🔄 Learning & Memory** — what they retain and patterns they recognize

## How to Use

### Claude Code
```bash
cp agents/personas/startup-cto.md ~/.claude/agents/
# Then: "Activate startup-cto mode"
```

### Cursor
```bash
./scripts/convert.sh --tool cursor
# Personas convert to .cursor/rules/*.mdc
```

### Any Supported Tool
```bash
./scripts/install.sh --tool <your-tool>
```

## Available Personas

| Persona | Emoji | Domain | Best For |
|---------|-------|--------|----------|
| [Startup CTO](startup-cto.md) | 🏗️ | Engineering + Strategy | Technical co-founders, architecture decisions, team building |
| [Growth Marketer](growth-marketer.md) | 🚀 | Marketing + Growth | Bootstrapped founders, content-led growth, launches |
| [Solo Founder](solo-founder.md) | 🦄 | Cross-domain | One-person startups, side projects, MVP building |

## Personas vs Task Agents

| | Task Agents (`agents/`) | Persona

*[truncated — see source for full prompt]*