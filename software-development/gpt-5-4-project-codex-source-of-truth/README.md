# GPT 5.4 PROJECT CODEX SOURCE OF TRUTH

> Updated: 2026-03-14
Repo: `C:\ANTIGRAVITY`
Primary branch: `main`
Current promoted baseline: `9796aba`

## Purpose

This file is the concise source-of

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GPT-5.4 Project Source Of Truth

Updated: 2026-03-14
Repo: `C:\ANTIGRAVITY`
Primary branch: `main`
Current promoted baseline: `9796aba`

## Purpose

This file is the concise source-of-truth brief for importing ANTIGRAVITY context into a ChatGPT project folder or other OpenAI workspace documentation.

It is designed to survive:
- accidental context loss
- machine rebuild
- node outage
- operator absence
- operator death

It intentionally contains paths, structure, and recovery logic, but not secret values.

## Live System Layout

- Live Codex base: `C:\ANTIGRAVITY`
- Live Codex workspace: `C:\ANTIGRAVITY\CodeX`
- Legacy local copy: `E:\ANTIGRAVITY` (not the live runtime base)
- Primary Git remote: `origin` -> GitHub `Trollz1004/ANTIGRAVITY`

## Node Topology

### SABRETOOTH

- Role: live Codex command post
- Runtime model: desktop-app-first
- Docker: not required
- Local fallback model: Ollama `qwen2.5:7b`
- Active scheduled tasks:
  - `CodeX-Fleet-Watcher`
  - `CodeX-Brain-Checkpoint`
  - `CodeX-Mission-Guardian`
  - `CodeX-Task-Sentry`
  - `CodeX-SABRETOOTH-Safe-Control`

### 9020

- Role: remote content/draft node
- Access: SSH reachable as `joshl`
- Boot mode: cold/quiet by default
- Approved scheduled task:
  - `CodeX-9020-Safe-Drafts`
- Policy: generates drafts and handoff files only, no live posting

### T5500

- Role: remote audit/revenue node
- Access: SSH reachable as `joshl`
- Boot mode: cold/quiet by default
- Still available intentionally: `qdrant` on `:6333`
- Approved scheduled tasks:
  - `CodeX-T5500-Safe-Marketing-Audit`
  - `CodeX-T5500-Revenue-Pack`

## MCP Connection Model

Two Codex MCP config files are part of the live setup:

- Repo MCP config: `C:\ANTIGRAVITY\.mcp.json`
- Workspace MCP config: `C:\ANTIGRAVITY\CodeX\.mcp.json`

Configured MCP servers:
- `antigravity-sentry`
- `filesystem`
- `github`
- `memory`
- `sequential-thinking`
- `puppeteer`
- `context7`

Important details:
- `antigravity-sentry` runs from `C:\ANTIGRAVITY\mcp-server\dis

*[truncated — see source for full prompt]*