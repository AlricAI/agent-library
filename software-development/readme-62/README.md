# README

> This directory contains YAML-based agent definitions for the CodeFRAME system.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Definitions

This directory contains YAML-based agent definitions for the CodeFRAME system.

## Overview

Agent definitions allow you to declaratively configure specialized agents with specific capabilities, system prompts, tools, and constraints. This enables:

- **Declarative Configuration**: Define agents in YAML instead of code
- **Easy Customization**: Modify agent behavior without changing source code
- **Version Control**: Track agent evolution through version-controlled YAML files
- **Rapid Prototyping**: Create new agent types quickly
- **Consistent Structure**: Standardized format for all agent definitions

## Directory Structure

```
definitions/
├── README.md                    # This file
├── backend-architect.yaml       # Built-in backend specialist
├── frontend-specialist.yaml     # Built-in frontend specialist
└── custom/                      # User-defined custom agents
    └── .gitkeep
```

## YAML Schema

### Required Fields

```yaml
name: unique-agent-identifier
type: agent-category
system_prompt: |
  Behavioral instructions for the agent...
```

### Optional Fields

```yaml
maturity: D2                     # D1, D2, D3, or D4
description: "Human-readable description"

capabilities:
  - Capability 1
  - Capability 2

tools:
  - tool_name_1
  - tool_name_2

constraints:
  max_tokens: 8000
  temperature: 0.7
  timeout_seconds: 300

metadata:
  version: "1.0.0"
  author: "Team Name"
  tags:
    - tag1
    - tag2
```

## Field Reference

### name (required)
- **Type**: string
- **Description**: Unique identifier for the agent
- **Example**: `backend-architect`, `frontend-specialist`

### type (required)
- **Type**: string
- **Description**: Agent category/classification
- **Common Values**: `backend`, `frontend`, `test`, `review`, `security`

### system_prompt (required)
- **Type**: string (multiline)
- **Description**: Behavioral instructions and expertise definition
- **Format**: Use YAML multiline syntax (`|`) for readability

### maturity

*[truncated — see source for full prompt]*