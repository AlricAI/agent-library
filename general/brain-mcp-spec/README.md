# BRAIN MCP SPEC

> Updated: 2026-03-23
Status: MVP scaffold created in repo
Canonical authority: `AGENTS.md`

## Purpose

BRAIN MCP is a LAN-local sidecar for shared ope

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# BRAIN MCP Specification

Updated: 2026-03-23
Status: MVP scaffold created in repo
Canonical authority: `AGENTS.md`

## Purpose

BRAIN MCP is a LAN-local sidecar for shared operational truth.

It exists to reduce drift between approved AI platforms by exposing:

- what is already built
- what is verified live
- what lane or drive a platform is allowed to use
- who is working where
- what changed and whether it was pushed
- what remains sandbox-only versus what has actually graduated into ANTIGRAVITY

BRAIN MCP is not governance, not a hierarchy, and not a replacement for any platform's own memory.

## What BRAIN Is

- shared operational memory
- lane and path awareness
- session check-in and check-out logging
- audit visibility for multi-node work
- a read-only mirror of repo truth files
- a way to answer the practical question: `Is this ANTIGRAVITY yet?`

## What BRAIN Is Not

- not canonical authority
- not a replacement for git
- not a replacement for `AGENTS.md`
- not a proxy in the LLM inference path
- not a secret store
- not a controller for Claude, Gemini, Codex, GitHub-approved repo workflows, or any other platform

Every BRAIN response must carry this authority notice:

`AGENTS.md is canonical. Josh is sole authority. BRAIN is operational telemetry only.`

## Memory Model

Platform and continuity memory remain where they already live:

- platform-specific memory remains with each platform
- shared repo truth remains in `C:\ANTIGRAVITY\memory` and `C:\ANTIGRAVITY\briefings`
- approved continuity snapshots remain in the locked OneDrive Personal Vault

BRAIN only synchronizes shared operational state and audit visibility.

## Live Repo Write Scope

The current live write scope for `C:\ANTIGRAVITY` is:

- OpenAI Codex
- Claude Code Opus
- Gemini CLI
- GitHub-approved repo workflows

These four are the only lanes currently allowed to write directly to the live repo.

BRAIN tracks the interactive clients directly:

- OpenAI Codex
- Claude Code Opus
- Gemini CLI

*[truncated — see source for full prompt]*