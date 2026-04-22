# API

> Comprehensive API documentation for the `cbw_foundry` Python package.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CloudCurio Framework API Reference

Comprehensive API documentation for the `cbw_foundry` Python package.

## Table of Contents

- [Overview](#overview)
- [Installation](#installation)
- [Core Modules](#core-modules)
- [CLI Modules](#cli-modules)
- [Runtime System](#runtime-system)
- [Specification System](#specification-system)
- [Observability](#observability)
- [Utilities](#utilities)
- [Usage Examples](#usage-examples)

## Overview

The `cbw_foundry` package is the core framework for CloudCurio, providing:

- **Agent Specification System**: Define and validate agent specs
- **Runtime Adapters**: Execute agents across multiple frameworks
- **CLI Tools**: Command-line interface for operations
- **Observability**: OpenTelemetry integration
- **Evaluation**: Golden test harness

### Package Structure

```
cbw_foundry/
├── cli.py              # Main CLI entry point
├── agent_cli.py        # Agent operations CLI
├── workflow_cli.py     # Workflow operations CLI
├── doctor_cli.py       # Health check CLI
├── capture_cli.py      # Scaffolding CLI
├── index_cli.py        # Registry management CLI
├── runtime/            # Runtime adapters
│   ├── base.py         # Abstract runtime interface
│   ├── local_runtime.py # Local execution
│   ├── adapters.py     # Framework bridges
│   ├── stubs.py        # Framework stubs
│   └── registry.py     # Component registration
├── spec/               # Specification system
│   ├── models.py       # Pydantic schemas
│   ├── io.py           # File I/O
│   └── compiler.py     # YAML→JSON compiler
├── observability/      # Monitoring
│   └── otel.py         # OpenTelemetry
├── evals/              # Evaluation
│   └── runner.py       # Test runner
└── util/               # Utilities
    └── fs.py           # Filesystem helpers
```

## Installation

```bash
# Basic installation
pip install -e .

# With development dependencies
pip install -e ".[dev]"

# In a virtual environment (recommended)
python -m venv .venv
source .venv/bin/activat

*[truncated — see source for full prompt]*