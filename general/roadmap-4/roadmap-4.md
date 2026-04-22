---
name: ROADMAP
description: ## Web UI Evolution

This document defines the recommended path for evolving Concerto's Web UI from the current
lightweight observability dashboard in
model: claude-sonnet-4-5
---
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
- retry queue inspection
- recent event streams
- operator actions such as refresh, retry, cleanup, and pause/resume in future phases

### Secondary path: `Leptos` with SSR/hydration

Consider this only if Concerto grows into a much more productized Web application with richer
component state and significantly more complex UI interactions.

Benefits:

- stronger component model
- more expressive client-side interactions
- full Rust end-to-end stack

Costs:

- higher build and runtime complexity
- more moving parts around SSR, hydration, and client behavior
- more application logic shifts toward UI code rather than staying service-centric

This should be a later migration option, not the next step.

### Not recommended as the main near-term path

- a separate SPA front end
- a React/Vite-style product shell
- a WASM-first Rust front end

These approaches add too much complexity for Concerto's current stage and operator-facing use case.

## Phased Roadmap

### Phase 1: Solidify the current server-rendered dashboard

Goal:

Make the existing Web UI genuinely useful for daily operator work without changing the rendering
model.

Add:

- HTML issue detail page at `/issues/:issue_identifier`
- richer summary cards for throughput, retries, rate limits, and last errors
- clearer visual grouping for running, retrying, and unhealthy states
- operator-focused details directly in HTML:
  - workspace path
  - recent events
  - last known error
  - retry due time
- reusable rendering helpers or template files so `src/web.rs` does not become a single large file

Acceptance criteria:

- an operator can understand system health from the HTML UI alone
- issue-specific debugging no longer requires raw JSON for common cases
- the rendering layer is organized enough to extend safely

### Phase 2: Introduce partial-page updates with `htmx`

Goal:

Improve interactivity and update ergonomics without converting the UI into a client-side app.

Add:

- route structure for HTML fragments, for example:
  - `/partials/dashboard`
  - `/partials/issues/:issue_identifier`
  - `/partials/retry-queue`
- `htmx`-driven operator actions:
  - refresh now
  - retry now
  - clear retry
  - cleanup workspace
- inline success/error feedback for operator actions
- partial refresh of key tables and cards instead of reloading the full page

Acceptance criteria:

- the dashboard updates without full page reloads for common actions
- error handling remains server-driven and easy to trace
- HTML remains readable and testable without browser-heavy infrastructure

### Phase 3: Add real-time streaming with SSE

Goal:

Deliver a live operator console feel while keeping the server authoritative.

Add:

- an SSE endpoint, for example `/events/stream`
- structured event types for:
  - snapshot updated
  - issue changed
  - retry queue changed
  - refresh queued
  - workflow reload failed
- server-side snapshot versioning or monotonic update ids
- client behavior that updates selected DOM regions on incoming events

Recommended model:

- SSE carries small event notifications and minimal payloads
- the browser updates targeted sections or requests a fresh HTML partial
- JSON API remains available for debugging and automation

Acceptance criteria:

- operators can observe runtime changes close to real time
- the streaming path does not become a second state machine distinct from the server
- disabling SSE still leaves the UI fully functional

### Phase 4: Expand from observability to operator workflows

Goal:

Turn the dashboard into a control surface, not just a viewer.

Possible additions:

- retry controls for stuck issues
- pause/resume orchestration
- issue filtering by state, priority, or error status
- workflow reload visibility and manual reload trigger
- workspace lifecycle controls
- log tail views or deep links to session logs

Constraints:

- keep operational actions explicit and auditable
- do not let the Web UI become required for orchestrator correctness
- preserve the current trust model unless a dedicated hardening project changes it

### Phase 5: Re-evaluate whether a richer UI stack is justified

Only after the previous phases are stable should Concerto evaluate a larger UI move such as
`Leptos`.

Trigger conditions for that decision:

- many pages with shared client-side state
- significantly richer data exploration needs
- complex interaction models that become awkward in HTML + `htmx`
- clear evidence that the operator UI has become a core product surface

If those conditions are not present, stay on the HTML-first path.

## Suggested Architecture

Target shape for the next iterations:

- `src/web.rs`
  - server bootstrap
  - router assembly
  - shared app state
- `src/web/handlers.rs`
  - dashboard handlers
  - issue detail handlers
  - action handlers
- `src/web/views.rs`
  - HTML rendering or template bindings
- `src/web/events.rs`
  - SSE event shaping
- `src/web/api.rs`
  - JSON API handlers and envelopes

This split should happen only when the current single-file implementation becomes difficult to
maintain. Avoid premature module proliferation.

## API and UI Principles

Keep these rules in place as the UI evolves:

- the Rust service is the source of truth
- the JSON API remains stable and automation-friendly
- HTML routes may consume the same snapshot/presenter layer as JSON
- operator actions should map to explicit backend operations
- do not duplicate state computation in the browser
- prefer small, obvious interfaces over a generalized front-end platform

## Risks To Avoid

- building a SPA too early
- coupling UI concerns directly into orchestrator logic
- introducing multiple sources of truth for runtime state
- making Web UI required for service correctness
- adding WebSocket or client state complexity before HTML + SSE limits are actually reached

## Near-Term Backlog

Recommended order of implementation:

1. Add HTML issue detail page
2. Refactor rendering out of the current single `src/web.rs`
3. Add richer health/error presentation to the dashboard
4. Add HTML partial routes and `htmx` actions
5. Add SSE endpoint and targeted live updates
6. Add operator controls for retries and workspace actions
7. Re-assess whether a heavier Rust UI framework is still necessary

## Decision

Concerto should continue on an HTML-first, Rust-owned Web UI path.

The default roadmap is:

- now: `axum` + server-rendered HTML
- next: templates + `htmx`
- then: SSE for live updates
- later, only if justified: `Leptos`