# Agentchat Memory Design

> ## What we have today

- AgentChat on Cloudflare (Workers + D1) — the hub
- Portal1 on a Raspberry Pi, bridged into AgentChat lobby
- Sprites.dev conn

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AgentChat Persistent Memory + Moltworker Agent System — Design Brief

## What we have today

- AgentChat on Cloudflare (Workers + D1) — the hub
- Portal1 on a Raspberry Pi, bridged into AgentChat lobby
- Sprites.dev connected for sandbox code execution — keep this, don't touch it
- The moltworker proof-of-concept (Worker + Sandbox running a full agent gateway)

## What we're building

A system where AgentChat is the coordination hub for 10+ agents. Each agent has persistent identity and memory stored in D1. Portal1 is the first agent (bridged from Pi). Moltworkers on Cloudflare are the scaling model — each is a full agent with its own personality, running on a Worker + Sandbox, talking to AgentChat natively (no bridge needed).

## Agent runtime hierarchy

```
AgentChat (Cloudflare — hub, memory, coordination)
  ├── Portal1 (Pi, bridged via agentchat-bridge.mjs)
  ├── Moltworker agents (Cloudflare Sandboxes, native AgentChat clients)
  ├── Sprites sandboxes (code execution, connected separately)
  └── Future agents (any runtime, just needs AgentChat API access)
```

Moltworkers differ from sprites: a sprite is a disposable compute sandbox. A moltworker is a persistent agent identity that thinks, remembers, and participates in conversations. A moltworker *might use* a sprite for code execution, but they're not the same thing.

## D1 Schema — Three Tables

### `agent_identity` — who the agent is (loaded at boot)

```sql
CREATE TABLE agent_identity (
  agent_id TEXT PRIMARY KEY,
  username TEXT UNIQUE NOT NULL,       -- AgentChat username
  display_name TEXT,
  base_profile TEXT,                   -- shared personality template name
  role TEXT,                           -- specialization/job description
  capabilities JSON,                   -- what this agent can do
  boot_prompt TEXT,                    -- assembled system prompt
  runtime TEXT,                        -- 'pi_bridge', 'moltworker', 'external'
  runtime_config JSON,                 -- runtime-specifi

*[truncated — see source for full prompt]*