# Skills Marketplace

> Skills are files that describe multi-step iPhone automation flows as intents, not scripts.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skills & Marketplace

Skills are files that describe multi-step iPhone automation flows as intents, not scripts. They can be written in **SKILL.md** format (recommended) or **YAML** format (legacy). The MCP server provides the tools; skills teach the AI what to do with them.

## Overview

The system has two layers:

1. **This repository** (`mirroir-mcp`) — provides 32 MCP tools for iPhone interaction
2. **Skill repositories** (e.g., [jfarcand/mirroir-skills](https://github.com/jfarcand/mirroir-skills)) — provide reusable skill files (SKILL.md or YAML) + plugin discovery

Skills are intentionally simple. Steps like `tap: "Email"` don't specify pixel coordinates — the AI uses `describe_screen` for fuzzy OCR matching and adapts to unexpected dialogs, layout changes, and timing differences.

## Plugin Discovery

Skills can be installed via AI coding assistant plugin systems or manually.

### Claude Code

```bash
claude plugin marketplace add jfarcand/mirroir-skills
claude plugin install skills@mirroir-skills
```

Plugin metadata lives in `.claude-plugin/marketplace.json` in the skill repository. The `SKILL.md` file in the skill repo teaches Claude how to interpret skill steps.

### GitHub Copilot CLI

```bash
copilot plugin marketplace add jfarcand/mirroir-skills
copilot plugin install skills@mirroir-skills
```

Plugin metadata lives in `.github/plugin/marketplace.json` in the skill repository.

### Manual Installation

Clone or copy skill files (`.md` or `.yaml`) into one of the scan directories:

```bash
# Global — available in all projects
git clone https://github.com/jfarcand/mirroir-skills.git \
    ~/.mirroir-mcp/skills/

# Project-local — available only in current project
mkdir -p .mirroir-mcp/skills/
cp my-skill.md .mirroir-mcp/skills/
```

Project-local skills with the same filename override global ones. When both a `.md` and `.yaml` file exist with the same stem name, the `.md` file takes precedence.

## Skill Format

Skills can be written in SKILL.md (recom

*[truncated — see source for full prompt]*