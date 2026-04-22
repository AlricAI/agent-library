# RUNTIME ADAPTERS

> Guide to implementing and using runtime adapters for different agent frameworks.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Runtime Adapters Guide

Guide to implementing and using runtime adapters for different agent frameworks.

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Supported Runtimes](#supported-runtimes)
- [Implementing Adapters](#implementing-adapters)
- [Configuration](#configuration)
- [Testing Adapters](#testing-adapters)

## Overview

Runtime adapters bridge CloudCurio agent specifications with different agent frameworks, enabling agents to run on multiple platforms without modification.

### Adapter Interface

All adapters implement the `BaseRuntime` interface:

```python
from abc import ABC, abstractmethod
from typing import Any, Dict
from dataclasses import dataclass


@dataclass
class RunResult:
    """Standard runtime execution result."""
    output: Any
    runtime: str
    metadata: Dict[str, Any] = None
    error: str = None


class AgentRuntime(ABC):
    """Base class for all runtime adapters."""
    
    name: str = "base"
    
    @abstractmethod
    def run(self, spec_path: str, user_input: str) -> RunResult:
        """
        Execute agent with given input.
        
        Args:
            spec_path: Path to agent specification
            user_input: Input for the agent
            
        Returns:
            RunResult with execution outcome
        """
        pass
```

## Architecture

### Runtime System

```
Agent Spec (YAML) → Runtime Adapter → Framework → LLM → Result
        ↓                  ↓              ↓         ↓       ↓
    Validate         Translate      Execute    Generate  Format
```

### Adapter Responsibilities

1. **Load Specification**: Parse and validate agent specs
2. **Configure Framework**: Set up framework-specific components
3. **Execute Agent**: Run agent with user input
4. **Handle Errors**: Manage framework errors gracefully
5. **Return Results**: Format output consistently

## Supported Runtimes

### Local Runtime

Built-in lightweight execution without external dependencies:

```pytho

*[truncated — see source for full prompt]*