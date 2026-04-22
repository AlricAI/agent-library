# TESTING GUIDE

> Comprehensive testing guide for CloudCurio agents, tools, and workflows.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Testing Guide

Comprehensive testing guide for CloudCurio agents, tools, and workflows.

## Table of Contents

- [Overview](#overview)
- [Testing Strategy](#testing-strategy)
- [Unit Testing](#unit-testing)
- [Integration Testing](#integration-testing)
- [Agent Evaluation](#agent-evaluation)
- [Performance Testing](#performance-testing)
- [Best Practices](#best-practices)

## Overview

CloudCurio uses a multi-layered testing approach:

1. **Unit Tests**: Test individual components
2. **Integration Tests**: Test component interactions
3. **Golden Tests**: Evaluate agent quality
4. **Performance Tests**: Measure performance metrics
5. **End-to-End Tests**: Test complete workflows

### Test Infrastructure

```bash
# Run all tests
make test

# Run specific test file
pytest tests/test_agent_spec.py

# Run with coverage
pytest --cov=cbw_foundry tests/

# Run integration tests
pytest -m integration tests/

# Run slow tests
pytest -m slow tests/
```

## Testing Strategy

### Test Pyramid

```
        ┌──────────────┐
        │  E2E Tests   │ ← Few, slow
        ├──────────────┤
        │  Integration │ ← Some, medium
        ├──────────────┤
        │ Unit Tests   │ ← Many, fast
        └──────────────┘
```

### Test Organization

```
tests/
├── unit/                    # Unit tests
│   ├── test_spec_models.py
│   ├── test_runtime.py
│   └── test_tools.py
├── integration/             # Integration tests
│   ├── test_agent_execution.py
│   └── test_workflow.py
├── evals/                   # Agent evaluations
│   └── test_agent_quality.py
├── performance/             # Performance tests
│   └── test_benchmarks.py
└── conftest.py             # Pytest configuration
```

## Unit Testing

### Testing Agent Specifications

```python
import pytest
from cbw_foundry.spec.models import AgentSpec, RuntimeConfig
from pydantic import ValidationError


class TestAgentSpec:
    """Test agent specification models."""
    
    def test_valid_spec_creation(self):
        """Test creating va

*[truncated — see source for full prompt]*