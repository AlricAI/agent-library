# TAURI

> The Bitterbot desktop app uses [Tauri 2](https://v2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Bitterbot Desktop — Tauri Shell

The Bitterbot desktop app uses [Tauri 2](https://v2.tauri.app/) to wrap the Control UI (Vite + React) in a native system-webview window and manage the gateway as a supervised child process. The result is one click → one window → the agent is running.

## Architecture

```
Tauri shell (Rust)
  ├─ system webview → Control UI (React SPA)
  └─ child process → node scripts/run-node.mjs gateway
                          └─ child process → bitterbot-orchestrator (P2P)
```

The Tauri shell does NOT embed the orchestrator as a Rust crate (yet). It spawns `node ... gateway` as a standard child process, and the gateway's `OrchestratorBridge` spawns the orchestrator in turn. The shell:

- Starts the gateway on launch, kills it on close
- Falls back gracefully if the gateway fails to start (the FirstRun / Disconnected UI still renders)
- On Unix, sends SIGINT for graceful gateway shutdown before SIGKILL
- On Windows, calls `kill()` directly (no SIGINT on Windows child processes)

## Prerequisites

### System-level (one time per machine)

**Rust toolchain** — same requirement as the orchestrator. Rust ≥ 1.88.

**Tauri system deps** — Tauri uses the OS system webview. Each platform needs different packages.

**Linux (Debian/Ubuntu):**

```bash
sudo apt-get update
sudo apt-get install -y \
  libwebkit2gtk-4.1-dev \
  libgtk-3-dev \
  libsoup-3.0-dev \
  libjavascriptcoregtk-4.1-dev \
  libglib2.0-dev \
  libayatana-appindicator3-dev \
  librsvg2-dev \
  patchelf
```

**macOS:** Xcode Command Line Tools (`xcode-select --install`). No extra packages.

**Windows:** Install [WebView2](https://developer.microsoft.com/en-us/microsoft-edge/webview2/). Most Windows 10/11 machines already have it.

### Node-level

```bash
cd desktop
pnpm install   # pulls @tauri-apps/cli as a devDep
```

## Development

```bash
# From the desktop/ directory:
pnpm tauri:dev
```

This does three things:

1. Starts the Vite dev server on `:5173` (same as `pnpm dev`)
2. Builds

*[truncated — see source for full prompt]*