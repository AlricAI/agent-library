# 03 Api

> REST API reference for agent execution, tool orchestration, and workflow management

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Server API Reference

## Overview

The agent server provides a REST API for AI agent execution, tool orchestration, workflow management, and intelligent query routing.

**Base URL**: `http://agent-lxc:8000`  
**Authentication**: JWT Bearer token  
**Content-Type**: `application/json`

## Authentication

All endpoints require a JWT Bearer token in the Authorization header:

```bash
Authorization: Bearer <jwt-token>
```

### Required Scopes

- `agent.execute` - Execute agents and workflows
- `agent.read` - Read agent/tool/workflow definitions
- `agent.write` - Create/update/delete definitions
- `admin.read` - Admin read access
- `admin.write` - Admin write access

## Endpoints

### Health Check

#### GET /health

Check service health.

**Authentication**: Not required

**Response**:
```json
{
  "status": "ok"
}
```

**Status Codes**:
- `200 OK` - Service healthy
- `503 Service Unavailable` - Service unhealthy

---

### Agent Management

#### GET /agents

List all agents (built-in + personal).

**Authentication**: Required  
**Scopes**: `agent.read`

**Query Parameters**:
- `is_builtin` (boolean, optional) - Filter by built-in status
- `is_active` (boolean, optional) - Filter by active status

**Response**:
```json
[
  {
    "id": "uuid",
    "name": "chat_agent",
    "display_name": "Chat Agent",
    "instructions": "You are a helpful assistant",
    "model": "agent",
    "tools": {"names": ["search_tool", "ingest_tool"]},
    "workflows": {"names": []},
    "scopes": ["search.read", "ingest.write"],
    "is_builtin": true,
    "created_by": null,
    "version": 1,
    "is_active": true,
    "created_at": "2025-12-12T10:00:00Z",
    "updated_at": "2025-12-12T10:00:00Z"
  }
]
```

**Status Codes**:
- `200 OK` - Success
- `401 Unauthorized` - Invalid/missing token
- `403 Forbidden` - Insufficient permissions

#### POST /agents/definitions

Create a new personal agent.

**Authentication**: Required  
**Scopes**: `agent.write`

**Request Body**:
```json
{
  "name"

*[truncated — see source for full prompt]*