# SIMPLE ASSIGNMENT APPROACH

> **Date**: 2025-10-19
**Status**: Production-ready for Sprint 4
**Location**: `codeframe/agents/simple_assignment.py`

---

## Overview

For Sprint 4 m

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Simple Agent Assignment - Sprint 4 Approach

**Date**: 2025-10-19
**Status**: Production-ready for Sprint 4
**Location**: `codeframe/agents/simple_assignment.py`

---

## Overview

For Sprint 4 multi-agent coordination, we're using a **simple keyword-based assignment** approach that is:

✅ **Simple** - Easy to understand and maintain
✅ **Robust** - 16 tests passing, handles edge cases
✅ **Non-blocking** - Won't create technical debt for future enhancements
✅ **Sufficient** - Works well for Sprint 4 demo requirements

**Future Enhancement**: Will be upgraded to capability-based routing in Sprint 9 (see `AGILE_SPRINTS.md` for details)

---

## How It Works

### Assignment Algorithm

```python
from codeframe.agents.simple_assignment import SimpleAgentAssigner

assigner = SimpleAgentAssigner()

task = {
    "title": "Create login form component",
    "description": "Build React component with Tailwind CSS"
}

agent_type = assigner.assign_agent_type(task)
# Result: "frontend-specialist"
```

**Process**:
1. Combine task title + description into lowercase text
2. Count keyword matches for each agent type
3. Return agent type with most matches
4. Default to "backend-worker" if no matches

---

## Agent Keywords

### Frontend Specialist
**Triggers**: `frontend, ui, ux, component, react, vue, angular, css, html, tailwind, styled, responsive, layout, button, form, modal, navigation, dashboard, chart, accessibility, a11y, wcag`

**Examples**:
- "Create login form component" → frontend
- "Build responsive dashboard UI" → frontend
- "Add WCAG accessibility features" → frontend

---

### Backend Worker
**Triggers**: `backend, api, endpoint, database, sql, orm, migration, schema, middleware, authentication, auth, server, service, controller, model, repository`

**Examples**:
- "Implement JWT middleware" → backend
- "Create database migration" → backend
- "Build REST API endpoint" → backend

---

### Test Engineer
**Triggers**: `test, testing, spec, unittest, integration test, e2

*[truncated — see source for full prompt]*