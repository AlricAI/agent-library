# ON DEMAND EXECUTION

> Azure HayMaker supports on-demand execution of scenarios via HTTP API, allowing operators to trigger specific scenarios without waiting for the scheduled runs (4x daily).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# On-Demand Execution API

Azure HayMaker supports on-demand execution of scenarios via HTTP API, allowing operators to trigger specific scenarios without waiting for the scheduled runs (4x daily).

## Table of Contents

- [Overview](#overview)
- [API Endpoints](#api-endpoints)
- [Authentication](#authentication)
- [Rate Limiting](#rate-limiting)
- [Usage Examples](#usage-examples)
- [Error Handling](#error-handling)
- [Implementation Details](#implementation-details)

## Overview

The on-demand execution feature provides:

- **HTTP API** for submitting execution requests
- **Rate limiting** to prevent abuse
- **Status tracking** via execution IDs
- **Asynchronous processing** using Service Bus queues
- **Progress monitoring** with status endpoints

### Architecture

```
Client Request → HTTP API → Rate Limiter → Execution Tracker
                                ↓
                          Service Bus Queue
                                ↓
                         Queue Processor
                                ↓
                    Container App Deployment
                                ↓
                         Status Updates
```

## API Endpoints

{: .note }
> The orchestrator uses a FastAPI-based REST API. See [API Reference](/AzureHayMaker/api/) for complete endpoint documentation.

### POST /api/execute

Submit an on-demand execution request.

**Request**:
```json
{
  "skip_validation": false
}
```

**Parameters**:
- `skip_validation` (optional): Skip environment validation (default: false)

**Response** (200 OK):
```json
{
  "execution_id": "3e598ac3-7b1b-46a6-8ddc-5986734e13fc",
  "status": "started",
  "started_at": "2025-11-25T04:52:29.217706+00:00"
}
```

**Error Responses**:
- `500 Internal Server Error`: Server error

### GET /api/executions/{execution_id}

Query the status of an execution.

**Request**:
```
GET /api/executions/3e598ac3-7b1b-46a6-8ddc-5986734e13fc
```

**Response** (200 OK):
```json
{
  "run_id": "3e598ac3-7b1b-46a6-8ddc-5986734e13fc

*[truncated — see source for full prompt]*