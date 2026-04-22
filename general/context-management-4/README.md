# Context Management

> **Feature**: 007-context-management
**Status**: Complete

## Overview

The Context Management system implements intelligent tiered memory (HOT/WARM/CO

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Context Management System

**Feature**: 007-context-management
**Status**: Complete

## Overview

The Context Management system implements intelligent tiered memory (HOT/WARM/COLD) with importance scoring to enable long-running autonomous agent sessions (4+ hours) by reducing token usage 30-50% through strategic context archival and restoration.

## Core Concepts

### Tiered Memory System

- **HOT Tier** (importance_score ≥ 0.8): Always loaded, critical context items
- **WARM Tier** (0.4 ≤ importance_score < 0.8): On-demand loading, semi-important items
- **COLD Tier** (importance_score < 0.4): Archived during flash save, rarely accessed

### Importance Scoring Algorithm

```python
score = 0.4 × type_weight + 0.4 × age_decay + 0.2 × access_boost

# Type weights: TASK (1.0), CODE (0.9), ERROR (0.8), PRD_SECTION (0.7), etc.
# Age decay: Exponential decay over time (half-life = 24 hours)
# Access boost: 0.1 per access, capped at 0.5
```

### Flash Save Mechanism

When context approaches token limit (80% of 180k = 144k tokens):

1. Create checkpoint with full context state (JSON serialization)
2. Archive COLD tier items (delete from active context)
3. Retain HOT and WARM tier items
4. Achieve 30-50% token reduction

## Usage Patterns

### 1. Creating Context Items

```python
from codeframe.agents.worker_agent import WorkerAgent
from codeframe.core.models import ContextItemType

agent = WorkerAgent(agent_id="backend-001", project_id=123, db=db)

# Save a task to context
await agent.save_context_item(
    item_type=ContextItemType.TASK,
    content="Implement user authentication with JWT tokens"
)

# Save code snippet
await agent.save_context_item(
    item_type=ContextItemType.CODE,
    content="def authenticate_user(token: str) -> User: ..."
)
```

### 2. Loading Context

```python
# Load all HOT tier items (always loaded)
hot_items = await agent.load_context(tier="hot")

# Load specific tier
warm_items = await agent.load_context(tier="warm", limit=50)

# Load all act

*[truncated — see source for full prompt]*