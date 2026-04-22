# 09 Swarm Intelligence Coordination

> ## Context

You are working on `packages/pump-agent-swarm/` in the crypto-vision monorepo. The intelligence layer (`src/intelligence/`) provides AI-dr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 09 — Pump Agent Swarm: Intelligence Layer & Coordination

## Context

You are working on `packages/pump-agent-swarm/` in the crypto-vision monorepo. The intelligence layer (`src/intelligence/`) provides AI-driven decision making, and the coordination layer (`src/coordination/`) orchestrates the swarm's lifecycle.

## Intelligence Files (`src/intelligence/`)

| File | Purpose |
|------|---------|
| `strategy-brain.ts` | Central decision maker — when to buy/sell/hold/exit |
| `signal-generator.ts` | Generates trading signals from multiple data sources |
| `risk-manager.ts` | Risk assessment and position sizing |
| `sentiment-analyzer.ts` | Analyzes market sentiment from social/on-chain data |
| `trend-detector.ts` | Detects price trends and momentum |
| `token-evaluator.ts` | Evaluates new tokens for opportunity scoring |
| `market-regime.ts` | Classifies market regime (bull/bear/sideways/volatile) |
| `alpha-scanner.ts` | Scans for alpha opportunities across Pump.fun |
| `narrative-generator.ts` | AI-generated token narratives and story arcs |
| `portfolio-optimizer.ts` | Optimizes allocation across tokens |

## Coordination Files (`src/coordination/`)

| File | Purpose |
|------|---------|
| `swarm-coordinator.ts` | Extended SwarmCoordinator with full lifecycle |
| `agent-messenger.ts` | Inter-agent communication via EventBus |
| `consensus-engine.ts` | Multi-agent consensus for trade decisions |
| `task-delegator.ts` | Assigns tasks to agents based on role/availability |
| `lifecycle-manager.ts` | Agent lifecycle: spawn, monitor, restart, shutdown |
| `health-monitor.ts` | Agent health checks and heartbeat monitoring |
| `phase-controller.ts` | State machine for swarm phases (18 states) |
| `rollback-manager.ts` | Handles failed operations and rollback |
| `audit-logger.ts` | Comprehensive audit trail for all actions |
| `config-manager.ts` | Dynamic configuration management |

## Task

### 1. Complete the Strategy Brain

The Strategy Brain is the AI core 

*[truncated — see source for full prompt]*