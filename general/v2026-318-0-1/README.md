# V2026.318.0

> > Released: 2026-03-18

## Highlights

- **Plugin framework and SDK** — Full plugin system with runtime lifecycle management, CLI tooling, settings UI

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# v2026.318.0

> Released: 2026-03-18

## Highlights

- **Plugin framework and SDK** — Full plugin system with runtime lifecycle management, CLI tooling, settings UI, breadcrumb and slot extensibility, domain event bridge, and a kitchen-sink example. The Plugin SDK now includes document CRUD methods and a testing harness. ([#904](https://github.com/paperclipai/paperclip/pull/904), [#910](https://github.com/paperclipai/paperclip/pull/910), [#912](https://github.com/paperclipai/paperclip/pull/912), [#909](https://github.com/paperclipai/paperclip/pull/909), [#1074](https://github.com/paperclipai/paperclip/pull/1074), @gsxdsm, @mvanhorn, @residentagent)
- **Upgraded costs and budgeting** — Improved cost tracking and budget management surfaces. ([#949](https://github.com/paperclipai/paperclip/pull/949))
- **Issue documents and attachments** — Issues now support inline document editing, file staging before creation, deep-linked documents, copy and download actions, and live-event refresh. ([#899](https://github.com/paperclipai/paperclip/pull/899))
- **Hermes agent adapter** — New `hermes_local` adapter brings support for the Hermes CLI as an agent backend. ([#587](https://github.com/paperclipai/paperclip/pull/587), @teknium1)
- **Execution workspaces (EXPERIMENTAL)** — Isolated execution workspaces for agent runs, including workspace operation tracking, reusable workspace deduplication, and work product management. Project-level workspace policies are configurable. ([#1038](https://github.com/paperclipai/paperclip/pull/1038))
- **Heartbeat token optimization** — Heartbeat cycles now skip redundant token usage.

## Improvements

- **Session compaction is adapter-aware** — Compaction logic now respects per-adapter context limits.
- **Company logos** — Upload and display company logos with SVG sanitization and enhanced security headers for asset responses. ([#162](https://github.com/paperclipai/paperclip/pull/162), @JonCSykes)
- **App version label** — The sidebar now displa

*[truncated — see source for full prompt]*