# MULTI AGENT GUIDE

> Comprehensive guide to building and using multi-agent systems in CloudCurio.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Multi-Agent Systems Guide

Comprehensive guide to building and using multi-agent systems in CloudCurio.

## Table of Contents

- [Overview](#overview)
- [Agent Types](#agent-types)
- [Coordination Patterns](#coordination-patterns)
- [Quick Start](#quick-start)
- [Examples](#examples)
- [Best Practices](#best-practices)

## Overview

CloudCurio provides a complete framework for building multi-agent systems with different coordination patterns:

- **Sequential**: Agents work in order, each building on previous results
- **Parallel**: Agents work simultaneously on independent tasks
- **Democratic**: Agents vote on decisions using confidence weighting
- **Hierarchical**: Coordinator delegates to workers and aggregates results

## Agent Types

### Coordinator Agents
**Role**: Orchestrate multi-agent workflows

**Capabilities**:
- Task decomposition
- Agent delegation
- Result aggregation
- Workflow management

**Example Agents**:
- `task_coordinator` - General purpose coordinator
- `project_manager` - Software project coordination

**System Prompt**: [prompts/agents/coordinator_system.md](../../../prompts/agents/coordinator_system.md)

### Worker Agents
**Role**: Execute specific tasks

**Capabilities**:
- Focused task execution
- Tool usage
- Quality output generation
- Progress reporting

**Example Agents**:
- `researcher` - Web research and information gathering
- `data_analyst` - Data processing and analysis
- `writer` - Content creation
- `developer` - Code generation

**System Prompt**: [prompts/agents/worker_system.md](../../../prompts/agents/worker_system.md)

### Reviewer Agents
**Role**: Quality assurance and validation

**Capabilities**:
- Work review and validation
- Quality assessment
- Improvement suggestions
- Standards compliance

**Example Agents**:
- `code_reviewer` - Code quality and security review
- `editor` - Content review and editing
- `qa_specialist` - Testing and quality assurance

**System Prompt**: [prompts/agents/reviewer_system.md](../../.

*[truncated — see source for full prompt]*