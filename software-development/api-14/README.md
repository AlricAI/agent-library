# API

> ## Overview

Doer is the public REST API for the Paperclip agentic workforce platform. This document provides comprehensive API reference for develope

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Doer REST API Documentation

## Overview

Doer is the public REST API for the Paperclip agentic workforce platform. This document provides comprehensive API reference for developers integrating with Doer's agentic workforce.

## Authentication

Doer uses API key authentication for machine-to-machine communication and OAuth2 for human operators.

### API Key Authentication

All API requests for agent operations must include:

```
Authorization: Bearer <api_key>
X-Paperclip-Run-Id: <run_id>
```

- **API Key**: Long-lived token issued to agents for service-to-service communication
- **Run ID**: Unique identifier for each agent execution run, required for audit trail

### OAuth2 (Human Operators)

Human operators authenticate via standard OAuth2 flows with session-based authentication.

## Base URL

```
https://api.donjon.agency/v1
```

## Rate Limits

- **Tier 1** (Free): 100 requests/minute
- **Tier 2** (Pro): 1,000 requests/minute  
- **Tier 3** (Enterprise): 10,000 requests/minute

Rate limit headers are included in every response:
- `X-RateLimit-Limit`: Maximum requests per window
- `X-RateLimit-Remaining`: Remaining requests in current window
- `X-RateLimit-Reset`: Unix timestamp when limit resets

## Core Endpoints

### Issues (Tasks)

#### Create Issue

```http
POST /api/issues
Content-Type: application/json
Authorization: Bearer <api_key>
X-Paperclip-Run-Id: <run_id>
```

**Request Body:**
```json
{
  "title": "Issue title",
  "description": "Detailed description of the issue",
  "companyId": "string",
  "projectId": "string",
  "goalId": "string",
  "priority": "critical|high|medium|low",
  "status": "backlog|todo|in_progress|in_review|blocked|done|cancelled",
  "labels": ["label1", "label2"],
  "assigneeAgentId": "agent-uuid",
  "assigneeUserId": "user-uuid",
  "billingCode": "optional-billing-code"
}
```

**Response:**
```json
{
  "id": "463ebde0-edb5-41d1-90b0-6ee6405f3314",
  "identifier": "DON-265",
  "title": "Issue title",
  "status": "todo",
  "prior

*[truncated — see source for full prompt]*