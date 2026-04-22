# 07 Swarm Agent Types

> ## Context

You are working on `packages/pump-agent-swarm/src/agents/` in the crypto-vision monorepo. There are 10 agent types (plus a market-maker ag

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 07 — Pump Agent Swarm: Complete All 10 Agent Types

## Context

You are working on `packages/pump-agent-swarm/src/agents/` in the crypto-vision monorepo. There are 10 agent types (plus a market-maker agent). Each agent is an autonomous actor in the swarm that operates on Solana's Pump.fun bonding curve.

The agents communicate via an `EventBus` (in `src/infra/event-bus.ts`) and are orchestrated by the `SwarmCoordinator` (in `src/swarm.ts`).

Key types from `src/types.ts`:
- `AgentRole`: creator | trader | analyst | sniper | market_maker | volume_bot | accumulator | exit_manager | sentinel | scanner | narrator
- `AgentIdentity`: { id, name, role, wallet, config, active, createdAt, lastHeartbeat }
- `TradeOrder`, `TradeResult`, `BondingCurveState`, `TradingStrategy`

The trading engine is in `src/trading/` with: `OrderRouter`, `PositionManager`, `PnLTracker`, `TradeScheduler`, `GasOptimizer`.

## Task

Review and complete each agent implementation. Every agent must:
1. Have a constructor that takes config + dependencies (wallet, RPC, event bus)
2. Implement a `start()` method that begins autonomous operation
3. Implement a `stop()` method for graceful shutdown
4. Emit events via the EventBus for monitoring
5. Handle errors with retry + backoff
6. Track its own stats (trades, success rate, PnL)
7. Follow the assigned `TradingStrategy` rules

### Agent Implementations

#### 1. Creator Agent (`creator-agent.ts`)
- Mints new tokens on Pump.fun using `createV2Instruction`
- Configures bonding curve parameters
- Executes atomic dev buy with the mint transaction
- Emits `token:created` event with `MintResult`

#### 2. Trader Agent (`trader-agent.ts`)
- Executes buy/sell orders on the bonding curve per strategy
- Respects `minIntervalSeconds`/`maxIntervalSeconds` between trades
- Respects `buySellRatio` for buy vs sell distribution
- Tracks position via `PositionManager`
- Stops when `maxTrades` or `maxDurationSeconds` reached
- Stops when budget exhausted

#### 3. S

*[truncated — see source for full prompt]*