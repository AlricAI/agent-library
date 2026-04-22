# Openapi Specifications

> **Category**: reference  
**Created**: 2025-12-12  
**Updated**: 2025-12-15  
**Status**: active

## Overview

This document provides an index of Open

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenAPI Specifications

**Category**: reference  
**Created**: 2025-12-12  
**Updated**: 2025-12-15  
**Status**: active

## Overview

This document provides an index of OpenAPI specifications for Busibox APIs and explains how to use them.

## Available Specifications

### AuthZ API
- **File**: `openapi/authz-api.yaml`
- **Service**: Authorization Service (authz-lxc)
- **Port**: 8010
- **Implementation**: `srv/authz/src/`
- **Description**: OAuth2-compliant authorization and authentication service with RBAC management

**Key Features**:
- OAuth2 token issuance (client_credentials and token-exchange grants)
- JWKS endpoint for token validation
- RBAC management (roles, users, permissions)
- OAuth client registry
- Audit logging
- User synchronization for first-party services

**Endpoints**:
- `/.well-known/jwks.json` - Public keys for JWT validation
- `/oauth/token` - OAuth2 token endpoint
- `/admin/roles` - Role management
- `/admin/user-roles` - User-role bindings
- `/admin/oauth-clients` - OAuth client management
- `/admin/users/{user_id}/roles` - User role queries
- `/internal/sync/user` - User sync from busibox-portal
- `/authz/audit` - Audit logging
- `/health` - Health checks

### Agent API
- **File**: `openapi/agent-api.yaml`
- **Service**: Agent Server (agent-lxc)
- **Port**: 8000
- **Implementation**: `srv/agent/app/`
- **Description**: Production-grade agent server with Pydantic AI for executing AI agents with tool calls, dynamic agent/workflow management, and token forwarding

**Key Features**:
- Dynamic agent definition management with personal/built-in agents
- Tool and workflow CRUD operations
- Agent run execution with SSE streaming
- Intelligent query routing via dispatcher
- Performance evaluation with scorers
- Schedule management for cron-based runs

**Endpoints**:
- `/agents` - Agent management
- `/agents/tools` - Tool management
- `/agents/workflows` - Workflow management
- `/agents/evals` - Evaluator management
- `/runs` - Run execution and m

*[truncated — see source for full prompt]*