# Testing Test Worktree

> This guide describes how to run tests in the test worktree (`/Users/joeflack4/projects/genonaut-wt2`) with isolated infrastructure that doesn't conflict with the main development worktree.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Test Worktree Testing Guide

This guide describes how to run tests in the test worktree (`/Users/joeflack4/projects/genonaut-wt2`) with isolated infrastructure that doesn't conflict with the main development worktree.

## Overview

When working in multiple git worktrees simultaneously, each worktree needs its own set of running services (API, Celery, Frontend) to avoid port conflicts and queue collisions. The test worktree uses dedicated ports and queue names while sharing the same test database.

## Architecture

### Main Worktree (`/Users/joeflack4/projects/genonaut`)
- ENV_TARGET: `local-test`
- API Port: 8001
- Frontend Port: 5173
- Redis DB: 3
- Redis Namespace: `genonaut_test`
- Celery Queues: `default`, `generation`
- Database: `genonaut_test`

### Test Worktree 2 (`/Users/joeflack4/projects/genonaut-wt2`)
- ENV_TARGET: `local-test-wt2`
- API Port: 8002
- Frontend Port: 5174
- Redis DB: 3 (same as main)
- Redis Namespace: `genonaut_test_wt2`
- Celery Queues: `default_wt2`, `generation_wt2`
- Database: `genonaut_test` (shared)

### Port and Queue Reference

| Service | Main Worktree | Test Worktree 2 | Alt Demo |
|---------|---------------|-----------------|----------|
| API | 8001 | 8002 | 8003 |
| Frontend | 5173 | 5174 | 5174 |
| Redis DB | 3 | 3 (shared) | 2 |
| Redis Namespace | genonaut_test | genonaut_test_wt2 | genonaut_demo |
| Celery Queues | default, generation | default_wt2, generation_wt2 | default, generation |
| Database | genonaut_test | genonaut_test | genonaut_demo |

## Quick Start

### 1. Start Worktree 2 Services

**Terminal 1: API Server**
```bash
cd /Users/joeflack4/projects/genonaut-wt2
make api-test-wt2
```

**Terminal 2: Celery Worker**
```bash
cd /Users/joeflack4/projects/genonaut-wt2
source env/python_venv/bin/activate  # Required: activate venv first
make celery-test-wt2
```

**Terminal 3: Frontend (optional, for E2E tests)**
```bash
cd /Users/joeflack4/projects/genonaut-wt2
make frontend-dev-wt2
```

### 2. Run Tests

**Terminal

*[truncated — see source for full prompt]*