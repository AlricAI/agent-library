# ENGINE TESTING

> This guide covers:

- how to build and start `tandem-engine`
- how to run automated tests
- how to run the end-to-end smoke/runtime proof flow on Wind

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Engine Build, Run, and Test Guide

This guide covers:

- how to build and start `tandem-engine`
- how to run automated tests
- how to run the end-to-end smoke/runtime proof flow on Windows, macOS, and Linux

## Windows quickstart (engine + tauri dev)

From `tandem/`:

```powershell
pnpm install
pnpm engine:stop:windows
cargo build -p tandem-ai
New-Item -ItemType Directory -Force -Path .\src-tauri\binaries | Out-Null
Copy-Item .\target\debug\tandem-engine.exe .\src-tauri\binaries\tandem-engine.exe -Force
pnpm tauri dev
```

## macOS/Linux quickstart (engine + tauri dev)

From `tandem/`:

```bash
pnpm install
# Kill any existing engine instance
pkill tandem-engine || true
cargo build -p tandem-ai
mkdir -p src-tauri/binaries
cp target/debug/tandem-engine src-tauri/binaries/tandem-engine
pnpm tauri dev
```

PowerShell equivalent (Windows):

```powershell
pnpm install
Get-Process | Where-Object { $_.ProcessName -in @('tandem-engine','tandem') } | Stop-Process -Force -ErrorAction SilentlyContinue
cargo build -p tandem-ai
New-Item -ItemType Directory -Force -Path .\src-tauri\binaries | Out-Null
Copy-Item .\target\debug\tandem-engine.exe .\src-tauri\binaries\tandem-engine.exe -Force
pnpm tauri dev
```

## Quick commands

From `tandem/`:

```bash
cargo build -p tandem-ai
cargo run -p tandem-ai -- serve --host 127.0.0.1 --port 39731
cargo test -p tandem-server -p tandem-core -p tandem-ai
```

# Testing with packages/tandem-control-panel

```bash
cargo build -p tandem-ai --profile fast-release
sudo install -m 755 target/fast-release/tandem-engine /usr/local/bin/tandem-engine
sudo systemctl restart tandem-engine
```

# Control panel testing locally

```bash
cd packages/tandem-control-panel && pnpm build && sudo systemctl restart tandem-control-panel.service && cd ../..
```

## API Token Security Validation

Verify token-gated API behavior:

```bash
cargo run -p tandem-ai -- serve --host 127.0.0.1 --port 39731 --state-dir .tandem --api-token tk_test_token
```

In a second term

*[truncated — see source for full prompt]*