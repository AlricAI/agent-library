# Http

> This document establishes the expected payloads and canonical behavior for the core HTTP API surface across all SDKs.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tandem Core HTTP Contracts

This document establishes the expected payloads and canonical behavior for the core HTTP API surface across all SDKs. Every SDK implemented must parse these exact shapes correctly.

## 1. Global Health (`/global/health`)

- **Method:** `GET`
- **Wire Response:** `{"ready": true, "phase": "startup"}`
- **SDK Normalized Response:** `SystemHealth`

## 2. Session List (`/session`)

- **Method:** `GET`
- **Wire Response:** `{"sessions": [{"id": "s_123", "title": "Example", "createdAtMs": 1700000000, "workspaceRoot": "/app"}], "count": 1}`
- **SDK Normalized Response:** `SessionListResponse` containing `[SessionRecord]`

## 3. Session Run Trigger (`/session/:id/prompt_async`)

- **Method:** `POST`
- **Input:** `{"parts": [{"type": "text", "text": "Prompt"}]}`
- **Wire Response:** `{"runID": "r_123"}`
- **Conflict Response (409):** `{"activeRun": {"runId": "r_123"}}`
- **SDK Normalized Response:** Parses canonical `runId` explicitly.

## 4. Key-Value Resources (`/resource`)

- **Method:** `GET`
- **Wire Response:** `{"items": [{"key": "status", "value": "active", "updatedAtMs": 1700000000}], "count": 1}`
- **SDK Normalized Response:** Canonical fields (`key`, `value`, `updatedAtMs` (TS) / `updated_at_ms` (Py)).

## 5. Global Memory (`/memory/*`)

- **Method:** `POST /memory/put`
- **Input:** `{"run_id":"r_123","user_id":"u_123","content":"Use sqlite WAL mode","source_type":"assistant_final","visibility":"private","project_tag":"repo-a","channel_tag":"web"}`
- **Wire Response:** `{"stored":true,"memoryID":"m_1","deduped":false}`
- **SDK Normalized Response:** `MemoryPutResponse` with compatibility for `memoryID`/`memory_id`.

- **Method:** `POST /memory/search`
- **Input:** `{"query":"sqlite wal","run_id":"r_123","user_id":"u_123","limit":5}`
- **Wire Response:** `{"results":[{"id":"m_1","content":"Use sqlite WAL mode","sourceType":"assistant_final","runId":"r_120","score":0.92}],"count":1}`
- **SDK Normalized Response:** Canonical memory recor

*[truncated — see source for full prompt]*