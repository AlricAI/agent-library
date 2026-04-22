# Telemetry Audit

> This document inventories all client-side telemetry (events, errors, logging) in the admin frontend and records the state before and after the SSOT implementation.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Frontend client telemetry audit

This document inventories all client-side telemetry (events, errors, logging) in the admin frontend and records the state before and after the SSOT implementation. "Client telemetry" = events/errors/metrics emitted by the frontend. "Telemetry (data)" = backend feeds (operator dashboard, snapshot, server telemetry) — see TelemetryContext.

## Sources found (pre-SSOT)

| Source | Location | Purpose |
|--------|----------|---------|
| **logFrontendError** | `frontend/admin/src/utils/logFrontendError.ts` | POST to `/api/v1/log/frontend-error` (fire-and-forget). Single call site: ErrorBoundary. No correlation IDs, no batching. |
| **resourceDebug** | `resourceDebug.ts`, `resourceRegistry.ts` | In-memory store of resource fetch status (loading/error/latency). ResourceDebugPanel (dev-only). Not an event pipeline. |
| **serversLogger** | `frontend/admin/src/utils/serversLogger.ts` | Console-only structured logs when `VITE_DEBUG_SERVERS=1`. Event-like: `servers_list_fetch`, `servers_sync`, `server_delete`, etc. Not sent to backend. |

## Third-party SDKs

None. No Sentry, PostHog, Datadog, Amplitude, Mixpanel, LogRocket.

## Duplicates / inconsistencies

- Two error/debug paths: logFrontendError (backend POST) vs resourceDebug (in-memory dev panel).
- serversLogger is a second, page-scoped event-like logger with snake_case event names; no shared schema.
- No single event catalog or validation.

## Event naming

- Only serversLogger had explicit event names; rest ad-hoc.
- After SSOT: stable catalog in `frontend/admin/src/telemetry/schema.ts` (page_view, api_request, api_error, frontend_error, user_action, plus servers_* for servers page).

## Missing context (pre-SSOT)

- No user/session/request ID on frontend-error payload.
- No correlation ID on API requests (shared createApiClient has no X-Request-ID).
- After SSOT: context (route, build_hash, etc.) and correlation_id on API events.

## Privacy / PII

- Backend contract: `docs/observabil

*[truncated — see source for full prompt]*