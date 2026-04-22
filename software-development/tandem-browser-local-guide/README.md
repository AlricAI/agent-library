# TANDEM BROWSER LOCAL GUIDE

> This file documents the current local `tandem-browser` build and the commands to test it on this machine.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tandem Browser Local Guide

This file documents the current local `tandem-browser` build and the commands to test it on this machine.

## Current local build paths

Current debug build:

```text
/home/user123/tandem/target/debug/tandem-browser
```

Current release build:

```text
/home/user123/tandem/target/release/tandem-browser
```

## Current browser detection on this host

The sidecar currently detects Chromium here:

```text
/snap/bin/chromium
```

The verified standalone doctor result is:

- `enabled: true`
- `runnable: true`
- `browser.path: /snap/bin/chromium`
- `blocking_issues: []`

## Standalone sidecar test

Run:

```bash
./target/debug/tandem-browser doctor --json
```

Expected result:

- `runnable: true`
- no blocking issues

## Engine-side readiness test

Run:

```bash
cargo run -p tandem-ai -- browser doctor --json
```

Expected result:

- `runnable: true`
- the engine sees the same browser setup that the standalone sidecar sees

## Full engine smoke test

Start the engine:

```bash
cargo run -p tandem-ai -- serve --hostname 127.0.0.1 --port 39731
```

In another terminal, check engine browser status:

```bash
cargo run -p tandem-ai -- browser status --hostname 127.0.0.1 --port 39731
curl -s http://127.0.0.1:39731/browser/status \
  -H 'Authorization: Bearer tk_3b9e2f1f5d194e46b4204f751acb9b27' | jq .
```

Expected result:

- browser status returns successfully
- `runnable: true`

If the engine is running with API token auth enabled, include the token on direct HTTP requests:

```bash
export TANDEM_API_TOKEN='tk_3b9e2f1f5d194e46b4204f751acb9b27'
curl -s http://127.0.0.1:39731/browser/status \
  -H "Authorization: Bearer $TANDEM_API_TOKEN" | jq .
```

## If `/browser/status` says browser automation is disabled

That means the engine process was started without browser automation enabled, even if the standalone `tandem-browser doctor --json` check passes.

For this machine, start the engine with browser automation explicitly enabled:

```bash
TANDEM_

*[truncated — see source for full prompt]*