# Docs.Acp

> This document describes how the OpenClaw ACP (Agent Client Protocol) bridge works,
how it maps ACP sessions to Gateway sessions, and how IDEs should i

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenClaw ACP Bridge

This document describes how the OpenClaw ACP (Agent Client Protocol) bridge works,
how it maps ACP sessions to Gateway sessions, and how IDEs should invoke it.

## Overview

`openclaw acp` exposes an ACP agent over stdio and forwards prompts to a running
OpenClaw Gateway over WebSocket. It keeps ACP session ids mapped to Gateway
session keys so IDEs can reconnect to the same agent transcript or reset it on
request.

Key goals:

- Minimal ACP surface area (stdio, NDJSON).
- Stable session mapping across reconnects.
- Works with existing Gateway session store (list/resolve/reset).
- Safe defaults (isolated ACP session keys by default).

## Bridge Scope

`openclaw acp` is a Gateway-backed ACP bridge, not a full ACP-native editor
runtime. It is designed to route IDE prompts into an existing OpenClaw Gateway
session with predictable session mapping and basic streaming updates.

## Compatibility Matrix

| ACP area                                                              | Status      | Notes                                                                                                                                                                                                                                            |
| --------------------------------------------------------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `initialize`, `newSession`, `prompt`, `cancel`                        | Implemented | Core bridge flow over stdio to Gateway chat/send + abort.                                                                                                                                                                                        |
| `listSessions`, slash commands                                        |

*[truncated — see source for full prompt]*