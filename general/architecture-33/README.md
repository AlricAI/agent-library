# ARCHITECTURE

> Dispatch is a two-component system: a Rust TUI (Console) that manages AI coding agents, and an Android app (Radio) that provides voice input over the local network.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Architecture

Dispatch is a two-component system: a Rust TUI (Console) that manages AI coding agents, and an Android app (Radio) that provides voice input over the local network.

## System Overview

```
┌──────────────────┐    TLS WebSocket (LAN, PSK)    ┌────────────────────────────┐
│  Dispatch Radio  │  <---------------------------> │  Dispatch Console          │
│  (Android)       │                                │                            │
│                  │                                │  Orchestrator (claude)     │
│  Volume keys     │   voice transcripts ───────>   │    ├─ receives transcripts │
│  SpeechRecognizer│   chat messages    <───────    │    ├─ issues tool calls    │
│  WebSocket client│   agent state      <───────    │    └─ decides all actions  │
│                  │                                │                            │
└──────────────────┘                                │  Agent PTYs (up to 26)     │
                                                    │    ├─ embedded terminals   │
                                                    │    ├─ git worktree each    │
                                                    │    └─ rendered in 2x2 grid │
                                                    └────────────────────────────┘
```

## Console (Rust)

### Crate Structure

The console is a Cargo workspace with two crates:

```
console/
├── Cargo.toml              # Binary crate: dispatch-console
├── config.default.toml     # Default config template
├── src/
│   ├── main.rs             # Event loop, startup, keyboard handling
│   ├── app.rs              # App state, tool execution
│   ├── pty.rs              # PTY spawn, read, kill, resize
│   ├── ui.rs               # TUI rendering (ratatui)
│   ├── ws_server.rs        # WebSocket server (tokio)
│   ├── config.rs           # Config loading, TLS cert generation
│   ├── types.rs            # Core types (Mode, SlotState, App)
│   ├── util.rs             # String cleanup, repo scannin

*[truncated — see source for full prompt]*