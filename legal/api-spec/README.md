# Api Spec

> ## Runtime Contract

- Public:
  - `GET /`
  - `GET /api/health`
  - `GET /api/status/providers`
- Protected routes require:
  - `Authorization: Beare

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Beyond Chat API Spec

## Runtime Contract

- Public:
  - `GET /`
  - `GET /api/health`
  - `GET /api/status/providers`
- Protected routes require:
  - `Authorization: Bearer <supabase_access_token>`
- Optional active-workspace header:
  - `X-Workspace-Id: <workspace-id>`

Hosted runtime authentication is Supabase-only. Local bypass is not part of the supported API contract.

## Response Conventions

- Some routes use `{ "data": ..., "error": null }`
- Some routes use route-specific payloads like `{ "workspace": ... }` or `{ "items": [...] }`
- Export routes return raw file responses

## Public Routes

### `GET /`

```json
{
  "service": "beyond-chat-backend",
  "status": "ok"
}
```

### `GET /api/health`

```json
{
  "status": "ok",
  "message": "Backend is reachable"
}
```

### `GET /api/status/providers`

```json
{
  "providers": {
    "openrouter": {
      "status": "connected",
      "label": "OpenRouter",
      "details": "..."
    }
  }
}
```

Valid provider states:

- `connected`
- `disconnected`
- `not_configured`
- `error`

## Auth And Workspace

### `POST /api/auth/bootstrap`

Ensures the authenticated user resolves to a workspace.

```json
{
  "data": {
    "workspace": {
      "id": "workspace-id",
      "name": "Beyond Chat Workspace",
      "created_at": "2026-04-09T00:00:00Z"
    },
    "role": "admin",
    "created": true,
    "source": "supabase_jwt"
  },
  "error": null
}
```

### `GET /api/workspace`

```json
{
  "workspace": {
    "id": "workspace-id",
    "name": "Beyond Chat Workspace",
    "created_at": "2026-04-09T00:00:00Z"
  },
  "authSource": "supabase_jwt"
}
```

### `GET /api/reminders`

```json
{
  "items": [
    {
      "id": "reminder-id",
      "title": "Follow up",
      "note": "Review the latest artifact",
      "due_at": "2026-04-10T09:00:00Z",
      "status": "open",
      "source": "internal",
      "workspace_id": "workspace-id",
      "created_at": "2026-04-09T00:00:00Z"
    }
  ]
}
```

## Chat

### `GET /api/chat/threads`

*[truncated — see source for full prompt]*