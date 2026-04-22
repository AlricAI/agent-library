# 03 Dashboard Trading Terminal

> ## Context

You are working on `crypto-vision`, a cryptocurrency intelligence platform. The dashboard is in `apps/dashboard/` (Next.js 15, Tailwind CS

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 03 — Dashboard Trading Terminal & Swarm Control

## Context

You are working on `crypto-vision`, a cryptocurrency intelligence platform. The dashboard is in `apps/dashboard/` (Next.js 15, Tailwind CSS). The backend has a full **Pump.fun Agent Swarm** in `packages/pump-agent-swarm/` with:

- 10 autonomous agent types (creator, trader, sniper, market maker, volume, accumulator, exit, narrative, scanner, sentinel)
- Jito bundle system (coordinator, validator, launch sequencer, anti-detection)
- Trading engine (order router, position manager, PnL tracker, wash engine, volume generator)
- Intelligence layer (strategy brain, signal generator, risk manager, sentiment analyzer)
- Dashboard API at port 3847 with REST + WebSocket
- 4 preset strategies: organic, volume, graduation, exit

The swarm's dashboard API exposes:
- `GET /api/status` — Phase, uptime, agents, trades, PnL
- `GET /api/agents` — All agents with stats
- `GET /api/agents/:id` — Agent detail + history
- `GET /api/trades` — Paginated trade history
- `GET /api/trades/flow` — Sankey flow data
- `GET /api/pnl` — PnL time series
- `GET /api/supply` — Token supply distribution
- `GET /api/events` — Filtered event timeline
- `GET /api/config` — Current config
- `PUT /api/config` — Update config
- `POST /api/actions/pause|resume|exit|emergency-stop` — Control actions
- `WS /ws` — Real-time event stream

The existing `apps/dashboard/src/app/swarm/page.tsx` has a basic swarm page. There are also existing components: `SwarmMonitor`, `SwarmStarter`.

## Task

### 1. Build the Trading Terminal Page (`/trading`)

Create a full-screen trading terminal at `/trading` with a multi-panel layout:

**Layout (resizable panels):**
```
┌──────────────────────────────────────────────────────────┐
│  Token: AIAC/SOL  │  Strategy: Organic  │  Phase: TRADING│
├────────────────────┬─────────────────────────────────────┤
│                    │                                     │
│   PRICE CHART      │   ORDER BOOK / BONDING CUR

*[truncated — see source for full prompt]*