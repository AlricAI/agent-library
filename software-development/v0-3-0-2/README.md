# V0.3.0

> > Released: 2026-03-09

## Highlights

- **New adapters: Cursor, OpenCode, and Pi** — Paperclip now supports three additional local coding agents. Cur

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# v0.3.0

> Released: 2026-03-09

## Highlights

- **New adapters: Cursor, OpenCode, and Pi** — Paperclip now supports three additional local coding agents. Cursor and OpenCode integrate as first-class adapters with model discovery, run-log streaming, and skill injection. Pi adds a local RPC mode with cost tracking. All three appear in the onboarding wizard alongside Claude Code and Codex. ([#62](https://github.com/paperclipai/paperclip/pull/62), [#141](https://github.com/paperclipai/paperclip/pull/141), [#240](https://github.com/paperclipai/paperclip/pull/240), [#183](https://github.com/paperclipai/paperclip/pull/183), @aaaaron, @Konan69, @richardanaya)
- **OpenClaw gateway adapter** — A new gateway-only OpenClaw flow replaces the legacy adapter. It uses strict SSE streaming, supports device-key pairing, and handles invite-based onboarding with join-token validation. ([#270](https://github.com/paperclipai/paperclip/pull/270))
- **Inbox and unread semantics** — Issues now track per-user read state. Unread indicators appear in the inbox, dashboard, and browser tab (blue dot). The inbox badge includes join requests and approvals, and inbox ordering is alert-focused. ([#196](https://github.com/paperclipai/paperclip/pull/196), @hougangdev)
- **PWA support** — The UI ships as an installable Progressive Web App with a service worker and enhanced manifest. The service worker uses a network-first strategy to prevent stale content.
- **Agent creation wizard** — A new choice modal and full-page configuration flow make it easier to add agents. The sidebar AGENTS header now has a quick-add button.

## Improvements

- **Mermaid diagrams in markdown** — Fenced `mermaid` blocks render as diagrams in issue comments and descriptions.
- **Live run output** — Run detail pages stream output over WebSocket in real time, with coalesced deltas and deduplicated feed items.
- **Copy comment as Markdown** — Each comment header has a one-click copy-as-markdown button.
- **Retry failed runs** 

*[truncated — see source for full prompt]*