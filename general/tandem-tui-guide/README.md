# TANDEM TUI GUIDE

> Compatibility note: This is a deep/legacy reference page.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tandem TUI Guide

Compatibility note: This is a deep/legacy reference page.
For the current user journey, start in `guide` at `tandem/guide/src/content/docs/tui-guide.md`.

The Tandem TUI (Terminal User Interface) provides a lightweight, keyboard-driven way to interact with the Tandem Engine.

## Running the TUI

To run the TUI, you must be in the `tandem` directory of the project.

```bash
cargo run -p tandem-tui --bin tandem-tui
```

### Connectivity Options

The TUI can interact with the Tandem Engine in two ways:

1. **Existing Instance**: If an engine is already running (e.g., from the desktop app or another terminal), the TUI will attempt to connect to it.
2. **Auto-Spawn**: If no engine is detected, the TUI will attempt to bootstrap and spawn a local engine process automatically.

## Startup Experience

On startup, you will see a short Matrix-style animation. You can skip this by pressing `Enter`, `Esc`, or `Space` once the engine bootstrap is ready.

### PIN Unlock

The TUI requires a **User PIN** to decrypt your locally stored provider keys (e.g., OpenAI, Anthropic keys).

- Enter your PIN when prompted.
- The input is masked for security.
- Once decrypted, your provider credentials are loaded into memory and synced with the engine.

## Usage & Controls

### Main Menu

When not in an active session, you are in the Main Menu.

- **j / Down**: Highlight next session.
- **k / Up**: Highlight previous session.
- **Enter**: Open selected session.
- **n**: Create a brand new session.
- **q**: Quit.

### Chat Interface

The chat interface is where you interact with agents.

#### Navigation & Layout

- **Tab**: Switch to the next agent pane.
- **BackTab**: Switch to the previous agent pane.
- **Alt + 1..9**: Jump directly to an agent by its number.
- **Alt + G**: Toggle between **Focus Mode** (one agent) and **Grid Mode** (multi-agent view).
- **[ / ]**: Previous/Next page in Grid Mode.
- **Up / Down**: Scroll message history.
- **PageUp / PageDown**: Page throug

*[truncated — see source for full prompt]*