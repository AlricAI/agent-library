# 08 Swarm Trading Engine Bundler

> ## Context

You are working on `packages/pump-agent-swarm/` in the crypto-vision monorepo. The trading engine (`src/trading/`) and bundle system (`src

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 08 — Pump Agent Swarm: Trading Engine & Bundle System

## Context

You are working on `packages/pump-agent-swarm/` in the crypto-vision monorepo. The trading engine (`src/trading/`) and bundle system (`src/bundle/`) are the core execution layer for all swarm operations on Solana.

## Trading Engine Files (`src/trading/`)

| File | Purpose |
|------|---------|
| `order-router.ts` | Routes orders to Pump.fun bonding curve or Jito bundles |
| `position-manager.ts` | Tracks open positions per agent, calculates unrealized PnL |
| `pnl-tracker.ts` | FIFO cost-basis P&L tracking |
| `trade-scheduler.ts` | Schedules trades per strategy (intervals, randomization) |
| `gas-optimizer.ts` | Optimizes priority fees and Jito tips |
| `slippage-calculator.ts` | Calculates expected slippage on bonding curve |
| `volume-generator.ts` | Generates organic-looking volume patterns |
| `wash-engine.ts` | Coordinates buy/sell wash trades across wallets |
| `wallet-rotation.ts` | Rotates wallets for anti-detection |
| `price-trajectory.ts` | Models expected price trajectory on bonding curve |
| `profit-consolidator.ts` | Consolidates profits from trader wallets to master |

## Bundle System Files (`src/bundle/`)

| File | Purpose |
|------|---------|
| `bundle-coordinator.ts` | Orchestrates multi-wallet bundle buys |
| `jito-client.ts` | Jito Block Engine client for bundle submission |
| `bundle-validator.ts` | Validates bundle transactions before submission |
| `launch-sequencer.ts` | Sequences the token launch: mint → dev buy → bundle buys |
| `supply-distributor.ts` | Distributes token supply across wallets |
| `anti-detection.ts` | Anti-detection patterns (timing, amounts, wallet age) |
| `timing-engine.ts` | Optimizes transaction timing for block inclusion |
| `dev-buy-optimizer.ts` | Optimizes the dev buy amount on curve |
| `wallet-funder.ts` | Funds trader wallets with SOL from master |
| `bundle-analytics.ts` | Tracks bundle success rates and costs |

## Task

### 1. Comp

*[truncated — see source for full prompt]*