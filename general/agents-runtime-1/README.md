# Agents Runtime

> Status: User-facing guide
Last updated: 2026-03-26
Audience: Operators setting up and running agents in Team Dashboard

## 1. What this system does

A

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Runtime Guide

Status: User-facing guide
Last updated: 2026-03-26
Audience: Operators setting up and running agents in Team Dashboard

## 1. What this system does

Agents in Team Dashboard do not run continuously.  
They run in **heartbeats**: short execution windows triggered by a wakeup.

Each heartbeat:

1. Starts the configured agent adapter (for example, Claude CLI or Codex CLI)
2. Gives it the current prompt/context
3. Lets it work until it exits, times out, or is cancelled
4. Stores results (status, token usage, errors, logs)
5. Updates the UI live

## 2. When an agent wakes up

An agent can be woken up in four ways:

- `timer`: scheduled interval (for example every 5 minutes)
- `assignment`: when work is assigned/checked out to that agent
- `on_demand`: manual wakeup (button/API)
- `automation`: system-triggered wakeup for future automations

If an agent is already running, new wakeups are merged (coalesced) instead of launching duplicate runs.

## 3. What to configure per agent

## 3.1 Adapter choice

Built-in adapters:

- `claude_local`: runs your local `claude` CLI
- `codex_local`: runs your local `codex` CLI
- `opencode_local`: runs your local `opencode` CLI
- `hermes_local`: runs your local `hermes` CLI
- `cursor`: runs Cursor in background mode
- `pi_local`: runs an embedded Pi agent locally
- `openclaw_gateway`: connects to an OpenClaw gateway endpoint
- `process`: generic shell command adapter
- `http`: calls an external HTTP endpoint

For local CLI adapters (`claude_local`, `codex_local`, `opencode_local`, `hermes_local`), Team Dashboard assumes the CLI is already installed and authenticated on the host machine.

## 3.2 Runtime behavior

In agent runtime settings, configure heartbeat policy:

- `enabled`: allow scheduled heartbeats
- `intervalSec`: timer interval (0 = disabled)
- `wakeOnAssignment`: wake when assigned work
- `wakeOnOnDemand`: allow ping-style on-demand wakeups
- `wakeOnAutomation`: allow system automation wakeups

## 3.3 Wor

*[truncated — see source for full prompt]*