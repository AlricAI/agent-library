# Telemetry

> Add `:telemetry` events at meaningful boundaries — where host apps need visibility
into launch flow health, service call latency, and cache effectiven

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Telemetry Instrumentation Plan

Add `:telemetry` events at meaningful boundaries — where host apps need visibility
into launch flow health, service call latency, and cache effectiveness.

## Design Principles

- Instrument at **boundaries**, not internals
- Don't duplicate what dependencies already emit (Req emits `[:req, :request, :*]`)
- Don't wrap storage adapter calls — that's host app code, they instrument their own
- Use **span** pattern (start/stop/exception) for operations with duration
- Use **single events** for instant observations (cache hit/miss)

## Events

### OIDC Flow (spans)

#### `[:ltix, :login, :start | :stop | :exception]`

Wraps `Ltix.handle_login/3`.

| Metadata       | Type     | Description                    |
| -------------- | -------- | ------------------------------ |
| `issuer`       | `String` | Platform issuer URL            |
| `client_id`    | `String` | Client ID from login params    |
| `redirect_uri` | `String` | Redirect URI from login params |

#### `[:ltix, :callback, :start | :stop | :exception]`

Wraps `Ltix.handle_callback/3`.

| Metadata        | Type     | Description                          |
| --------------- | -------- | ------------------------------------ |
| `issuer`        | `String` | From verified token (stop only)      |
| `client_id`     | `String` | From verified token (stop only)      |
| `deployment_id` | `String` | From verified token (stop only)      |
| `message_type`  | `String` | e.g. `LtiResourceLinkRequest` (stop) |

### Advantage Services (spans)

#### `[:ltix, :grade_service, <action>, :start | :stop | :exception]`

Actions: `:list_line_items`, `:get_line_item`, `:create_line_item`,
`:update_line_item`, `:delete_line_item`, `:post_score`, `:get_results`

| Metadata   | Type     | Description          |
| ---------- | -------- | -------------------- |
| `endpoint` | `String` | Service endpoint URL |

#### `[:ltix, :memberships_service, <action>, :start | :stop | :exception]`

Actions: `:get_memb

*[truncated — see source for full prompt]*