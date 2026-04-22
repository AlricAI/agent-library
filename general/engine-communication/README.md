# ENGINE COMMUNICATION

> This document explains how Tandem clients communicate with `tandem-engine`, how runs stream, and how desktop/TUI coordinate engine lifecycle.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Engine Communication Guide

This document explains how Tandem clients communicate with `tandem-engine`, how runs stream, and how desktop/TUI coordinate engine lifecycle.

## Components

- `tandem-engine` (Rust binary): the shared HTTP + SSE runtime and source of truth.
- Tauri desktop app (`src/` + `src-tauri/`): the native client shell; its root `index.html` is the desktop UI entrypoint, and it starts/stops an engine sidecar when needed.
- TUI (`crates/tandem-tui`): a terminal client that attaches to an existing engine when available, otherwise bootstraps/spawns one.
- Web control panel (`packages/tandem-control-panel/`): a browser-based client plus service bootstrap layer that connects to the same engine runtime.

## Default Endpoint Strategy

- Host: `127.0.0.1`
- Default port: `39731` (moved away from `3000` to avoid common frontend dev collisions)
- Desktop sidecar behavior:

1. Prefer configured/default port.
2. If unavailable, fall back to an ephemeral local port.

- TUI behavior:

1. Try configured/default base URL first.
2. If not healthy, spawn engine with configured/default port.

## Environment Overrides

- `TANDEM_ENGINE_PORT`
  - Engine CLI `serve` default (`--port`) via clap env binding.
  - Desktop sidecar preferred port default.
  - TUI connect/spawn port default.
- `TANDEM_ENGINE_HOST`
  - Engine CLI `serve` default (`--hostname`) via clap env binding.
- `TANDEM_ENGINE_URL`
  - TUI explicit base URL override (takes precedence over host/port composition).
- `TANDEM_API_TOKEN`
  - When set, engine requires `Authorization: Bearer <token>` or `X-Tandem-Token: <token>` for API calls (except health).
- `TANDEM_SHARED_ENGINE_MODE`
  - Desktop/TUI shared-engine behavior toggle.

## Runtime API Surface (High Level)

Core session/run endpoints:

- `POST /session` create session
- `GET /session` list sessions
- `POST /session/{id}/message` append message
- `POST /session/{id}/prompt_async` start async run
- `POST /session/{id}/prompt_sync` sync run path
- `

*[truncated — see source for full prompt]*