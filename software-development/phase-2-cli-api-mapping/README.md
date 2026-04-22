# PHASE 2 CLI API MAPPING

> **Created:** 2026-02-01
**Issue:** #322 - Server Layer Refactor
**Branch:** phase-2/server-layer

This document ensures 1:1 mapping between CLI comman

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Phase 2: CLI-to-API Route Mapping

**Created:** 2026-02-01
**Issue:** #322 - Server Layer Refactor
**Branch:** phase-2/server-layer

This document ensures 1:1 mapping between CLI commands and v2 server routes.

---

## 1. Golden Path Commands (Priority)

These are the core workflow commands from `docs/GOLDEN_PATH.md`.

| CLI Command | Core Module | Core Function | V2 Route | Method | Status |
|-------------|-------------|---------------|----------|--------|--------|
| `cf init <repo>` | `core.workspace` | `create_or_load_workspace()` | `/api/v2/workspaces` | POST | ⚠️ Missing |
| `cf init --detect` | `core.workspace` | `create_or_load_workspace()` | `/api/v2/workspaces` | POST | ⚠️ Missing |
| `cf status` | `core.project_status` | `get_workspace_status()` | `/api/v2/projects/status` | GET | ✅ Present |

### PRD Commands

PRD has two workflows:
1. **Discovery** - Interactive Socratic generation (`cf prd generate`)
2. **CRUD** - Direct management of stored PRDs (`cf prd add/show/list/delete`)

Both end up with PRD records managed by `core.prd`.

| CLI Command | Core Module | Core Function | V2 Route | Method | Status |
|-------------|-------------|---------------|----------|--------|--------|
| `cf prd generate` | `core.prd_discovery` | `start_discovery_session()` | `/api/v2/discovery/start` | POST | ✅ Present |
| (answer question) | `core.prd_discovery` | `process_answer()` | `/api/v2/discovery/{id}/answer` | POST | ✅ Present |
| (generate from session) | `core.prd_discovery` | `generate_prd()` | `/api/v2/discovery/{id}/generate-prd` | POST | ✅ Present |
| `cf prd add <file>` | `core.prd` | `store()` | `/api/v2/prd` | POST | ✅ Present |
| `cf prd show` | `core.prd` | `get_latest()` | `/api/v2/prd/latest` | GET | ✅ Present |
| `cf prd list` | `core.prd` | `list_all()` | `/api/v2/prd` | GET | ✅ Present |
| `cf prd delete` | `core.prd` | `delete()` | `/api/v2/prd/{id}` | DELETE | ✅ Present |
| `cf prd export` | `core.prd` | `export_to_file()` | (CLI-only) | - | N/A |


*[truncated — see source for full prompt]*