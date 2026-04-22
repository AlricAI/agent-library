# QUICKSTART

> ## 5-Minute Setup

### 1. Create Your First Agent Definition

Create a file `codeframe/agents/definitions/custom/my-agent.yaml`:

```yaml
name: my-spe

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Definition Loader - Quick Start Guide

## 5-Minute Setup

### 1. Create Your First Agent Definition

Create a file `codeframe/agents/definitions/custom/my-agent.yaml`:

```yaml
name: my-specialist
type: custom
description: "My custom agent for specific tasks"

capabilities:
  - Task A
  - Task B
  - Task C

system_prompt: |
  You are a specialist in...

  Focus on quality and best practices.

tools:
  - tool_1
  - tool_2

constraints:
  max_tokens: 5000
  temperature: 0.7
```

### 2. Load and Use Your Agent

```python
from pathlib import Path
from codeframe.agents.definition_loader import AgentDefinitionLoader

# Initialize loader
loader = AgentDefinitionLoader()

# Load all definitions
loader.load_definitions(Path("codeframe/agents/definitions"))

# Create your agent
agent = loader.create_agent(
    agent_type="my-specialist",
    agent_id="my-agent-001"
)

# Use the agent
print(f"Created {agent.agent_id}")
print(f"System prompt: {agent.definition.system_prompt}")
```

### 3. Query Available Agents

```python
# List all available
available = loader.list_available_types()
print(f"Available: {available}")

# Get specific definition
definition = loader.get_definition("my-specialist")
print(f"Capabilities: {definition.capabilities}")

# Query by type
custom_agents = loader.get_definitions_by_type("custom")
```

## YAML Schema Cheat Sheet

### Minimal Valid Definition
```yaml
name: agent-name
type: agent-type
system_prompt: "Instructions for agent"
```

### Complete Definition
```yaml
name: agent-name
type: agent-type
maturity: D2                    # D1, D2, D3, or D4
description: "Description"

capabilities:
  - Capability 1
  - Capability 2

system_prompt: |
  Multi-line
  behavioral instructions

tools:
  - tool_name_1
  - tool_name_2

constraints:
  max_tokens: 8000
  temperature: 0.7
  timeout_seconds: 300

metadata:
  version: "1.0.0"
  author: "Your Name"
  tags: [tag1, tag2]
```

## Common Use Cases

### Backend Developer Agent
```yaml
name: backend-dev

*[truncated — see source for full prompt]*