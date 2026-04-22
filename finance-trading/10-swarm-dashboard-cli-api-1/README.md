# 10 Swarm Dashboard Cli Api

> ## Context

You are working on `packages/pump-agent-swarm/` in the crypto-vision monorepo. The swarm has a built-in monitoring stack:

- `src/dashboar

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 10 — Pump Agent Swarm: Dashboard, CLI, API & Telegram

## Context

You are working on `packages/pump-agent-swarm/` in the crypto-vision monorepo. The swarm has a built-in monitoring stack:

- `src/dashboard/` — Real-time dashboard with Hono API server + WebSocket
- `src/api/` — Screener API server (x402-gated analytics)
- `src/cli.ts` — Interactive CLI
- `src/telegram/` — Telegram bot integration
- `src/demo/` — Demo mode for presentations

## Task

### 1. Complete the Dashboard Server (`src/dashboard/server.ts`)

The dashboard server runs on port 3847 and provides REST + WebSocket:

```typescript
// Dashboard Server should:
// 1. Hono app with CORS enabled
// 2. Serve an inline HTML dashboard at GET / (dark-themed, single page)
// 3. REST endpoints (all prefixed /api):
//    GET /api/status — SwarmStatus
//    GET /api/agents — Agent summaries
//    GET /api/agents/:id — Agent detail + performance history
//    GET /api/trades — Paginated trades (query: limit, offset, agent, direction)
//    GET /api/trades/flow — Sankey trade flow data
//    GET /api/pnl — PnL time series + snapshot
//    GET /api/pnl/agents — Per-agent PnL
//    GET /api/supply — Supply distribution
//    GET /api/config — Current config + schema
//    GET /api/health — Full health report
//    GET /api/events — Filtered events (query: category, severity, agent, from, to, search)
//    GET /api/audit — Audit trail
//    GET /api/export/:format — Export (json/csv/markdown/full)
//    PUT /api/config — Update config (validated)
//    POST /api/actions/pause — Pause swarm
//    POST /api/actions/resume — Resume
//    POST /api/actions/exit — Trigger exit
//    POST /api/actions/emergency-stop — Emergency stop
// 4. Optional API key auth for write endpoints
// 5. WebSocket at /ws for real-time events
```

### 2. Complete the WebSocket Handler (`src/dashboard/websocket.ts`)

```typescript
// WebSocket handler should:
// 1. Accept WebSocket upgrades at /ws
// 2. Send periodic status updates ev

*[truncated — see source for full prompt]*