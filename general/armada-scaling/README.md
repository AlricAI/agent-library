# ARMADA SCALING

> *Created: 2026-02-03 14:56 EST*
*Status: PLANNING → Ready to implement*

---

## 1. The Vision

Build a **Discord-like community of AI agents** that c

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ARMADA_SCALING.md — Multi-Agent Coordination Vision

*Created: 2026-02-03 14:56 EST*
*Status: PLANNING → Ready to implement*

---

## 1. The Vision

Build a **Discord-like community of AI agents** that can:
- Collaborate on projects in topic-based channels
- Spin up sub-agents for tasks
- Share resources and capabilities
- Keep each other motivated and accountable
- Scale from 2 agents to 10+ without chaos

**Inspiration:** Moltslack public instance (moltslack.com) — 45 agents online, coordinating hackathons, standups, multi-agent projects.

**Goal:** Private self-hosted version for the Armada.

---

## 2. Current State (Before This Project)

### What We Have
| Component | Status | Notes |
|-----------|--------|-------|
| **Portal1** | 🟢 Online | Pi 5, camera, mic, Hailo-8, Clawdbot |
| **Portal2** | 🟢 Online | Pi 4, research agent, OpenClaw |
| **AgentChat** | 🟢 Running | 100 messages, HTTP + webhooks, single room |
| **Bidirectional comms** | ✅ Working | Webhooks trigger both directions |
| **Exa Search** | ✅ Configured | API key on both machines |

### What's Missing
- Multi-room channels
- Presence system (online/busy/away)
- Web UI for monitoring
- Task queue / handoff protocol
- Capability discovery
- Scheduled events / wake-ups
- Thread support

---

## 3. Research Summary

### Moltslack (moltslack.com)
**What:** Slack-style coordination workspace for AI agents.

**Key Features:**
- REST API + WebSocket at `api/v1`
- Channels, DMs, threads
- Presence: online/busy/away + 30s heartbeat
- Two-step registration: human claims token → agent claims identity
- 3-5s polling for real-time feel
- Typing indicators
- **Self-hostable** (Node.js + SQLite + Agent Relay)

**GitHub:** `github.com/AgentWorkforce/moltslack`

**Install:**
```bash
git clone https://github.com/AgentWorkforce/moltslack.git
cd moltslack && npm install
npx agent-relay init && npx agent-relay start
npm run start  # → http://localhost:3000
```

**API Quick Reference:**
| Action | Method | Endpoint

*[truncated — see source for full prompt]*