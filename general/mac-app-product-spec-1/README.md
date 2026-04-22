# Mac App Product Spec

> Status: canonical product spec for the first-party Mac app

## Summary

The first-party `MLXR` Mac app is the unified native consumer shell over the
s

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MLXR Mac App Product Spec

Status: canonical product spec for the first-party Mac app

## Summary

The first-party `MLXR` Mac app is the unified native consumer shell over the
shared runtime.

Current implementation status:

- native Swift package scaffold exists in `packages/clients/mlxr-mac-app/`
- runtime bridge, feature shells, and early tests are real
- the app now has a shared global composer, a project-first `Library`, rail-
  based `Activity`, guided starter-model setup, and no separate `Studio`
  destination in the visible or internal shell
- polish, onboarding, packaging, and release hardening still remain

Its job is to make the current runtime accessible to non-technical Mac users
without creating a second architecture or a host-owned inference stack.

## Product Goals

- zero-complication local use on a Mac
- clear generate, edit, and iteration flows
- straightforward progress, outputs, and errors
- one thin client over the same runtime used by the CLI

## Technology Direction

- native macOS app
- SwiftUI first, with AppKit interop only where needed
- shared runtime access over the local UDS-backed runtime contract
- on-demand runtime startup or attachment handled by the app

Do not build the first app as:

- a second local inference implementation
- a Tauri or Electron shell with duplicated runtime logic
- a special-case path that bypasses the shared runtime

## Development Path

Use a real dev `.app` bundle as the normal local workflow.

The canonical repo command is:

```bash
uv run python scripts/dev.py mac-app
```

That command should stay the default because it gives the app a stable macOS
identity, which is important for windowing, debugging, and Peekaboo-driven UI
automation. Direct `swift run` is still useful for package-only debugging, but
it should not be the main product-development path.

## Product Boundary

The first app should expose real and supported runtime capabilities on day one.

That means:

- promoted defaults are easy to find

*[truncated — see source for full prompt]*