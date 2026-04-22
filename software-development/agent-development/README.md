# AGENT DEVELOPMENT

> Complete guide to developing agents in the CloudCurio framework.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Development Guide

Complete guide to developing agents in the CloudCurio framework.

## Table of Contents

- [Overview](#overview)
- [Agent Specification Format](#agent-specification-format)
- [Creating Your First Agent](#creating-your-first-agent)
- [Agent Architecture](#agent-architecture)
- [Tool Integration](#tool-integration)
- [Model Configuration](#model-configuration)
- [Testing & Evaluation](#testing--evaluation)
- [Best Practices](#best-practices)
- [Advanced Patterns](#advanced-patterns)

## Overview

CloudCurio agents are defined using a declarative YAML specification format that compiles to optimized JSON artifacts for execution. This approach provides:

- **Human-friendly authoring**: Write specs in readable YAML
- **Machine-optimized execution**: Run from compiled JSON
- **Framework agnostic**: Support multiple runtime adapters
- **Type safety**: Pydantic validation ensures correctness
- **Testability**: Golden test suites for reliable validation

### Agent Lifecycle

```
YAML Spec → Validation → Compilation → Runtime Execution → Evaluation
     ↓           ↓            ↓              ↓               ↓
   Author    Check Valid   JSON Artifact   Execute       Test Quality
```

## Agent Specification Format

### Schema v1 Structure

```yaml
api_version: v1              # Specification version
kind: Agent                  # Resource type
metadata:                    # Agent metadata
  name: agent_name          # Unique identifier (lowercase_snake_case)
  version: 1.0.0            # Semantic version
  tags: [domain, type]      # Classification tags
spec:                        # Agent specification
  model_policy:             # Model configuration
    preferred:              # Primary model
      provider: ollama      # Provider (ollama, openai, anthropic, etc.)
      model: qwen2.5-coder  # Model identifier
    fallbacks: []           # Fallback models (optional)
  prompts:                  # Prompt configuration
    system: path/to/prompt.md  # 

*[truncated — see source for full prompt]*