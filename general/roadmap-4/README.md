# ROADMAP

> ## Web UI Evolution

This document defines the recommended path for evolving Concerto's Web UI from the current
lightweight observability dashboard in

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Concerto Roadmap

## Web UI Evolution

This document defines the recommended path for evolving Concerto's Web UI from the current
lightweight observability dashboard into a more complete operator-facing interface, while keeping
the Rust service as the primary state owner.

## Current State

Concerto currently provides:

- a local HTTP server powered by `axum`
- a server-rendered HTML dashboard at `/`
- JSON observability endpoints under `/api/v1/*`
- lightweight refresh behavior suitable for debugging and local operations

This is intentionally simple and appropriate for the current project phase. The next steps should
improve usability and real-time visibility without introducing a front-end architecture that is
heavier than the product needs.

## Recommendation

The recommended direction is:

- keep `axum` as the HTTP foundation
- keep Rust as the primary source of truth for UI state
- add a server-side HTML rendering layer using a small Rust-native templating approach
- add `htmx` for partial-page updates and operator actions
- add SSE for live state streaming where real-time updates are useful

This is the best fit for Concerto because:

- the current application is service-first, not UI-first
- the core value is observability and control, not rich client-side state
- it keeps the system easy to debug from logs and HTML output
- it avoids introducing a second complex application inside the repo

## Why This Stack

### Primary path: `axum` + templates + `htmx` + SSE

Use this as the default roadmap.

Benefits:

- minimal architecture churn from the current implementation
- Rust service remains the owner of runtime state and rendering decisions
- HTML-first development is a good fit for dashboards and operator panels
- SSE provides real-time updates without the complexity of a full SPA or WebSocket-heavy client
- `htmx` adds interactivity without moving state management into the browser

Recommended use cases:

- dashboard summary
- issue detail pages
- retry qu

*[truncated — see source for full prompt]*