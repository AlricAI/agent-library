# V2026.403.0

> > Released: 2026-04-03

## Highlights

- **Execution workspaces** — Full workspace lifecycle management for agent runs: workspace-aware routine runs, 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# v2026.403.0

> Released: 2026-04-03

## Highlights

- **Execution workspaces** — Full workspace lifecycle management for agent runs: workspace-aware routine runs, execution workspace detail pages with linked issues, runtime controls (start/stop), close readiness checks, and follow-up issue workspace inheritance. Project workspaces get their own detail pages and a dedicated tab on the project view. ([#2074](https://github.com/paperclipai/paperclip/pull/2074), [#2203](https://github.com/paperclipai/paperclip/pull/2203))
- **Inbox overhaul** — New "Mine" inbox tab with mail-client keyboard shortcuts (j/k navigation, a/y archive, o open), swipe-to-archive, "Mark all as read" button, operator search with keyboard controls, and a "Today" divider. Read/dismissed state now extends to all inbox item types. ([#2072](https://github.com/paperclipai/paperclip/pull/2072), [#2540](https://github.com/paperclipai/paperclip/pull/2540))
- **Telemetry** — App-side telemetry sender with periodic flush, graceful shutdown, plugin telemetry bridge, and server-side telemetry aligned with the backend schema. Agent role is used in task-completed events. ([#2527](https://github.com/paperclipai/paperclip/pull/2527))
- **Feedback and evals** — Thumbs-up/down feedback capture flow with voting UI, feedback modal styling, and run link placement in the feedback row. ([#2529](https://github.com/paperclipai/paperclip/pull/2529))
- **Document revisions** — Issue document revision history with a restore flow, replay-safe migrations, and revision tracking API. ([#2317](https://github.com/paperclipai/paperclip/pull/2317))

## Improvements

- **Optimistic comments** — Comments render instantly with optimistic IDs while the server confirms; draft clearing is fixed for a smoother composing experience.
- **Comment interrupts** — New interrupt support for issue comments with queued comment thread UX. The interrupt checkbox was later removed in favor of a cleaner flow.
- **GitHub Enterprise URL support** — Sk

*[truncated — see source for full prompt]*