# ENGINE CLI

> This guide documents the master `tandem` CLI and the direct `tandem-engine`
runtime using bash commands (macOS/Linux/WSL).

## Quick Start

```bash
ta

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tandem Engine CLI Guide

This guide documents the master `tandem` CLI and the direct `tandem-engine`
runtime using bash commands (macOS/Linux/WSL).

## Quick Start

```bash
tandem --help
tandem doctor
tandem status
tandem service install
tandem install panel
tandem panel init
tandem panel open
tandem-engine serve --hostname 127.0.0.1 --port 39731
tandem run "Summarize this repository"
```

For the official headless bootstrap path, use the master CLI:

```bash
npm i -g @frumu/tandem
tandem install panel
tandem panel init
```

For a direct engine-only setup, install the master CLI and start the runtime:

```bash
npm i -g @frumu/tandem
tandem-engine serve --hostname 127.0.0.1 --port 39731
```

If you need a terminal-first interface instead, install the TUI:

```bash
npm i -g @frumu/tandem-tui
tandem-tui
```

## Command Overview

### `serve`

Starts the HTTP/SSE runtime used by desktop and TUI clients.

```bash
tandem-engine serve --hostname 127.0.0.1 --port 39731
```

Useful options:

- `--hostname` (alias: `--host`)
- `--port`
- `--state-dir`
- `--provider`
- `--model`
- `--api-key`
- `--config`
- `TANDEM_ENGINE_HOST` (env override)
- `TANDEM_ENGINE_PORT` (env override)
- `TANDEM_API_TOKEN` (optional API auth token requirement)

The master CLI also understands `tandem service status`, `tandem update`,
`tandem addon list`, and `tandem panel open` for the add-on flow.

### `status`

Checks engine health by calling `GET /global/health`.

```bash
tandem-engine status
tandem-engine status --hostname 127.0.0.1 --port 39731
```

## Engine-Detected Execution Environment

Engine runtime now detects host environment once at startup and treats it as canonical:

- `os`: `windows|linux|macos`
- `shell_family`: `powershell|posix`
- `path_style`: `windows|posix`
- `arch`: host architecture (for example `x86_64`, `aarch64`)

This environment is injected into run prompts, exposed via `GET /global/health` (`environment`),
and attached to `session.run.started` events so all clients (D

*[truncated — see source for full prompt]*