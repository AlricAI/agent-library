# SWARM ARCHITECTURE

> Multi-agent coordination system for CloudCurio.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Swarm Architecture

Multi-agent coordination system for CloudCurio.

## Table of Contents

- [Overview](#overview)
- [Core Concepts](#core-concepts)
- [Architecture](#architecture)
- [Implementation](#implementation)
- [Communication](#communication)
- [Coordination Patterns](#coordination-patterns)

## Overview

The Swarm subsystem provides distributed multi-agent coordination, enabling agents to collaborate on complex tasks through structured communication and governance.

### Key Features

- **Distributed Coordination**: Agents coordinate without centralized control
- **Democratic Decision Making**: Confidence-weighted voting for quality
- **Task Decomposition**: Break complex tasks into agent-specific subtasks
- **State Management**: Shared knowledge base with conflict resolution
- **Quality Assurance**: Built-in governance and quality checks

## Core Concepts

### Swarm

Collection of agents working toward a common goal:

```python
from cbw_foundry.swarm import Swarm, SwarmConfig

swarm = Swarm(
    name="content_pipeline",
    agents=[generator, reviewer, publisher],
    config=SwarmConfig(
        coordination_mode="democratic",
        max_iterations=10,
        quality_threshold=0.8
    )
)

result = swarm.execute(task="Create blog post about AI")
```

### Agent Roles

Agents in swarms have specific roles:

- **Coordinator**: Manages task flow and delegation
- **Worker**: Executes specific subtasks
- **Reviewer**: Quality checks and validation
- **Specialist**: Domain-specific expertise

### Communication

Agents communicate through structured messages:

```python
from cbw_foundry.swarm.communication import Message, MessageType

message = Message(
    type=MessageType.TASK_REQUEST,
    sender="coordinator_agent",
    recipient="worker_agent",
    content={
        "task": "Generate content",
        "deadline": "2026-01-24T12:00:00Z"
    }
)
```

## Architecture

### System Components

```
┌─────────────────────────────────────────┐
│           Swarm Orch

*[truncated — see source for full prompt]*