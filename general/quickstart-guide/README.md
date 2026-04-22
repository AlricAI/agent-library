# QUICKSTART GUIDE

> Get started with CloudCurio agents, tools, and workflows in 15 minutes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CloudCurio Quick Start Guide

Get started with CloudCurio agents, tools, and workflows in 15 minutes.

## Prerequisites

- Python 3.10+
- Ollama running locally (for LLM tools)
- Git

## Installation

```bash
# Clone repository
cd ~/Documents/cloudcurio_monorepo/cloudcurio-monorepo

# Bootstrap (creates venv, installs dependencies)
./scripts/bootstrap.sh

# Activate virtual environment
source venv/bin/activate

# Verify installation
make doctor
```

## Your First Agent

### 1. Create Agent Specification

Create `agents/specs/my_first_agent.agent.yaml`:

```yaml
api_version: v1
kind: Agent
metadata:
  name: my_first_agent
  version: 1.0.0
  description: My first CloudCurio agent
  tags: [quickstart]

spec:
  model_policy:
    preferred:
      provider: ollama
      model: qwen2.5-coder
  
  prompts:
    system: |
      You are a helpful assistant that can search the web and process data.
      Be concise and accurate in your responses.
  
  tools:
    - id: web_search
      type: python
      entrypoint: agents/tools/web_tools.py:search_engine_tool
    
    - id: llm_completion
      type: python
      entrypoint: agents/tools/llm_tools.py:llm_completion_tool
      config:
        temperature: 0.7
  
  runtime:
    supported: [local]
    timeout: 300
```

### 2. Validate Agent

```bash
./bin/cbw-agent validate agents/specs/my_first_agent.agent.yaml
```

### 3. Run Agent

```bash
./bin/cbw-agent run agents/specs/my_first_agent.agent.yaml \
  --input "Search for information about Python async programming" \
  --runtime local
```

## Your First Multi-Agent System

### 1. Create Swarm Script

Create `my_swarm.py`:

```python
#!/usr/bin/env python3
"""My first multi-agent swarm."""

from cbw_foundry.swarm import Swarm, SwarmAgent, SwarmConfig, CoordinationMode

# Create agents
agents = [
    SwarmAgent(
        name="researcher",
        role="worker",
        capabilities=["research"],
        confidence=0.9
    ),
    SwarmAgent(
        name="summarizer",
        rol

*[truncated — see source for full prompt]*