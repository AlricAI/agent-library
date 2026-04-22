# AGENT FACTORY GUIDE

> ## Overview

The Agent Factory system provides a declarative, YAML-based approach to defining and creating agents in CodeFRAME. Instead of hardcoding 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Factory System Guide

## Overview

The Agent Factory system provides a declarative, YAML-based approach to defining and creating agents in CodeFRAME. Instead of hardcoding agent configurations, you define them in YAML files and use the factory to instantiate them dynamically.

## Architecture

### Components

1. **AgentDefinitionLoader** (`codeframe/agents/definition_loader.py`)
   - Loads and validates YAML agent definitions
   - Manages definition cache
   - Supports built-in and custom definitions

2. **AgentFactory** (`codeframe/agents/factory.py`)
   - Creates WorkerAgent instances from definitions
   - Provides convenience methods for listing and querying agents
   - Handles backward compatibility

3. **YAML Definitions** (`codeframe/agents/definitions/`)
   - Built-in definitions: `*.yaml` in definitions directory
   - Custom definitions: `*.yaml` in `custom/` subdirectory
   - Custom definitions override built-in ones with same name

4. **WorkerAgent** (`codeframe/agents/worker_agent.py`)
   - Enhanced to accept `system_prompt` parameter
   - Maintains backward compatibility with existing code

## YAML Definition Format

### Required Fields

```yaml
name: agent-name           # Unique identifier
type: agent-type          # Category (backend, frontend, test, review)
system_prompt: |          # Agent behavioral instructions
  You are an expert in...
```

### Optional Fields

```yaml
maturity: D2              # D1-D4 maturity level (default: D1)
description: "..."        # Human-readable description

capabilities:             # List of capabilities
  - Capability 1
  - Capability 2

tools:                    # Available tools
  - tool_name_1
  - tool_name_2

constraints:              # Execution constraints
  max_tokens: 8000
  temperature: 0.7
  timeout_seconds: 300

metadata:                 # Additional metadata
  version: "1.0.0"
  author: "Team Name"
  tags:
    - tag1
    - tag2
```

## Usage Examples

### Basic Usage

```python
from codeframe.age

*[truncated — see source for full prompt]*