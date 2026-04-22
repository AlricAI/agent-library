# Phase2 Proactive Intelligence

> ## Overview

Phase 2 introduces three autonomous capabilities:

1. Bug Hunter: turns bug issues into executable failing Vitest tests.
2. Leak Plumber:

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Phase 2: Proactive Intelligence Architecture

## Overview

Phase 2 introduces three autonomous capabilities:

1. Bug Hunter: turns bug issues into executable failing Vitest tests.
2. Leak Plumber: immediately scans newly public repositories and contains incidents.
3. Live Surgery: launches browser-based code-server sessions for interactive debugging.

## Runtime Topology

- Worker (`backend/src/index.ts` + routes): event ingest + orchestration + GitHub/Cloudflare API actions.
- Container Control Plane (`container/src/server.ts`, port `8788`): command execution, git checkout, file ops, process inspection.
- Debug Plane (`code-server`, port `8080`): proxied interactive IDE sessions with tokenized session URLs.

## Feature Design

### 1) Bug Hunter

- Trigger: `issues` webhook where `action=opened` and label includes `bug`.
- Worker flow:
  - Parse issue body with Gemini (`@google/genai`) to extract reproducible structure.
  - Generate a failing `reproduction.test.ts` via Gemini structured output.
  - Use sandbox execution APIs to:
    - clone repo with installation token,
    - write `reproduction.test.ts`,
    - run `vitest run reproduction.test.ts`.
  - Decision:
    - non-zero exit code -> reproduction confirmed.
    - zero exit code -> reproduction not yet confirmed.
  - Action: post GitHub issue comment with test code + test output.

### 2) Leak Plumber

- Trigger: `repository` webhook on public transition (`publicized`, `public`, or `private=true -> false`).
- Worker flow:
  - Run `trufflehog git --json` in sandbox against authenticated repo URL.
  - If findings exist:
    - call GitHub API to set `private: true`,
    - attempt Cloudflare Worker secret rotation for compromised bindings (value-matching + heuristics),
    - open incident issue for audit trail.

### 3) Live Surgery

- Trigger: frontend POST to `/api/ops/:operationId/debug/start`.
- Worker flow:
  - Start code-server on sandbox debug port.
  - Register exposed debug port against session token.
  -

*[truncated — see source for full prompt]*