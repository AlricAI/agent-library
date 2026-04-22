# 04 Testing

> Unit, integration, and e2e testing guide for the agent server

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Server Testing Guide

## Overview

The agent server has comprehensive test coverage with unit, integration, and e2e tests. Tests can be run locally during development or on deployed infrastructure.

## Quick Start

### Local Testing

```bash
# Setup virtual environment (first time only)
cd /Users/wessonnenreich/Code/sonnenreich/busibox/srv/agent
bash scripts/setup-venv.sh
source venv/bin/activate

# Run all tests
make test

# Run specific test suites
make test-unit           # Fast, isolated unit tests
make test-integration    # Integration tests with DB
make test-cov            # Tests with coverage report
```

### Deployed Testing (via MCP)

```bash
# From busibox/provision/ansible directory

# Test environment
make test-agent INV=inventory/staging
make test-agent-unit INV=inventory/staging
make test-agent-integration INV=inventory/staging
make test-agent-coverage INV=inventory/staging

# Production environment
make test-agent
make test-agent-unit
make test-agent-integration
make test-agent-coverage

# Interactive test menu
make test-menu
```

## Test Structure

```
tests/
├── conftest.py              # Shared fixtures (DB, auth, agents)
├── test_health.py           # Smoke test
├── unit/                    # Fast, isolated tests
│   ├── test_auth_tokens.py  # JWT validation, claims
│   ├── test_token_service.py # Token caching/exchange
│   ├── test_busibox_client.py # HTTP client
│   ├── test_agents_core.py  # Agent validation
│   ├── test_run_service.py  # Run execution logic
│   ├── test_dispatcher.py   # Dispatcher schema validation
│   ├── test_dynamic_loader.py # Dynamic agent loading
│   ├── test_scheduler.py    # Scheduled runs
│   ├── test_workflow_engine.py # Workflow execution
│   └── test_scorer_service.py # Performance evaluation
└── integration/             # Tests with real DB
    ├── test_api_runs.py     # Runs API endpoints
    ├── test_api_streams.py  # SSE streaming
    ├── test_api_agents.py   # Agent CRUD
    ├── test_api_schedule.py #

*[truncated — see source for full prompt]*