# Agent Skills

> ## Overview

Agent Skills is a lightweight, markdown-based format for defining modular, reusable agent capabilities. Introduced by Anthropic in Decemb

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Skills

## Overview

Agent Skills is a lightweight, markdown-based format for defining modular, reusable agent capabilities. Introduced by Anthropic in December 2024, Agent Skills enables you to specialize agents without modifying code by loading skill definitions from simple `SKILL.md` files.

Swarms implements full support for the Agent Skills standard, making it **compatible with Anthropic's Claude Code** and other tools that use the same format.

## Key Benefits

- **Modular**: Skills are separate files, easy to create, share, and maintain
- **Reusable**: Build skill libraries for common tasks across your organization
- **Portable**: Standard format works across platforms and tools
- **Simple**: Just markdown files with YAML frontmatter - no code needed
- **Compatible**: Works with Anthropic's Agent Skills ecosystem

## SKILL.md Format

Skills are defined using a simple structure:

```yaml
---
name: skill-name
description: A clear description of what this skill does
---

# Skill Name

Instructions that guide the agent's behavior when this skill is active.

## Guidelines
- Guideline 1
- Guideline 2

## Examples
- Example usage 1
- Example usage 2
```

### Required Components

1. **YAML Frontmatter**:
   - `name`: Unique identifier for the skill (lowercase, hyphens for spaces)
   - `description`: Clear description of what the skill does and when to use it

2. **Markdown Content**: Detailed instructions, guidelines, examples, and methodologies

## Quick Start

### Basic Usage

```python
from swarms import Agent

# Create agent with skills
agent = Agent(
    agent_name="Financial Analyst",
    model_name="gpt-4o",
    skills_dir="./example_skills",  # Point to your skills directory
    max_loops=1
)

# Agent automatically follows skill instructions
response = agent.run("Perform a DCF valuation for Apple")
```

### Directory Structure

```
example_skills/
├── financial-analysis/
│   └── SKILL.md
├── code-review/
│   └── SKILL.md
└── data-visualization/
    └─

*[truncated — see source for full prompt]*