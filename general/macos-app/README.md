# Macos App

> This repo can be built as a local macOS app bundle that launches the existing
web UI on `127.0.0.1` and keeps all writable state under the user runtim

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# macOS App

This repo can be built as a local macOS app bundle that launches the existing
web UI on `127.0.0.1` and keeps all writable state under the user runtime
home.

## Build

Install dependencies first:

```bash
uv sync
```

Build the `.app` bundle with PyInstaller:

```bash
uv run --with pyinstaller python scripts/build_mac_app.py
```

Build a local `.dmg` release artifact:

```bash
uv run python scripts/build_mac_dmg.py --tag v1.0.0
```

Bundle output:

```text
dist/Job Application Assistant.app
```

DMG output:

```text
dist/Job-Application-Assistant-v1.0.0-macos.dmg
```

The DMG name uses the release tag (for example,
`Job-Application-Assistant-<tag>-macos.dmg`). The current DMG is unsigned, so
Gatekeeper may warn until signing and notarization are added later. GitHub
releases can include the macOS DMG for distribution.

## What The Bundle Contains

The build includes the runtime resources that still need to exist as files at
execution time:

- `scripts/static/`
- `scripts/prompts/`
- `assets/fonts/`
- `governance/runtime-policy.json`

Internal Python subprocesses are routed through
`scripts/runtime_entrypoints.py`, so packaged mode does not depend on raw
source-script paths.

## Runtime Model

The packaged app is a launcher around the same backend used by the local web
app. It does not create a second settings system.

- `scripts/mac_app_launcher.py` prepares runtime-home directories, loads local
  env files, configures trace processors, resolves a local port, and starts
  the FastAPI app.
- `scripts/web_settings_api.py` exposes the same settings and onboarding API
  used by the local web surface.
- `scripts/runtime_policy.py` enforces policy-as-code decisions for shared
  actions such as settings saves, material imports, worker control, provider
  calls, and live submit.
- `scripts/runtime_trace.py` registers redacted JSONL processors at startup so
  governed actions emit local traces without leaking secrets or prompt bodies.

## Runtime Home

When pack

*[truncated — see source for full prompt]*