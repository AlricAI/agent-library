# FASTAPI ROUTER ANALYSIS

> **Analyst**: FastAPI Architecture Expert
**Date**: 2025-12-11
**File Analyzed**: `/home/frankbria/projects/codeframe/codeframe/ui/server.py` (4,161 li

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# FastAPI Router Refactoring - Architecture Assessment

**Analyst**: FastAPI Architecture Expert
**Date**: 2025-12-11
**File Analyzed**: `/home/frankbria/projects/codeframe/codeframe/ui/server.py` (4,161 lines)
**Total Endpoints**: 65 endpoints (63 REST + 1 WebSocket + 1 root health check)

---

## Executive Summary

The current server.py is a **monolithic FastAPI application** with 65 endpoints organized into 11 functional domains. The refactoring from monolith to APIRouter-based architecture is **highly feasible** with **moderate complexity**. The main challenges are:

1. **Shared State Dependencies** - 3 module-level singletons (`app.state.db`, `running_agents`, `manager`)
2. **WebSocket Broadcasting** - `ConnectionManager` used across multiple endpoint groups
3. **Background Task Orchestration** - `BackgroundTasks` with cross-domain side effects
4. **Import Cycles Risk** - If routers need to import from each other or shared state utilities

**Recommended Approach**: Extract routers in 3 waves (simple → medium → complex) with dependency injection for shared state.

---

## 1. Current Routing Patterns

### 1.1 Endpoint Organization

FastAPI tags already provide logical grouping (though not consistently applied):

| Tag Category | Endpoint Count | Prefix Pattern | Notes |
|-------------|----------------|----------------|-------|
| **Projects** (untagged) | 14 | `/api/projects/*` | Core CRUD + agent assignment |
| **Context** | 6 | `/api/agents/{id}/context/*` | Context management (T067) |
| **Review** | 6 | `/api/agents/{id}/review/*`, `/api/tasks/{id}/reviews` | Code review system |
| **Checkpoints** | 6 | `/api/projects/{id}/checkpoints/*` | Checkpoint/restore |
| **Lint** | 4 | `/api/lint/*` | Linting results |
| **Metrics** | 3 | `/api/projects/{id}/metrics/*`, `/api/agents/{id}/metrics` | Token usage & costs |
| **Quality Gates** | 2 | `/api/tasks/{id}/quality-gates` | Pre-completion checks |
| **Session** | 1 | `/api/projects/{id}/session` | Session state |
|

*[truncated — see source for full prompt]*