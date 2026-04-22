# 06 Swarm Fix Builds Types

> ## Context

You are working on `packages/pump-agent-swarm/` in the crypto-vision monorepo. This is an autonomous Solana trading swarm for Pump.fun tok

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 06 — Pump Agent Swarm: Fix Builds, Types & Dependencies

## Context

You are working on `packages/pump-agent-swarm/` in the crypto-vision monorepo. This is an autonomous Solana trading swarm for Pump.fun tokens. It has ~62K lines of code across 86 files but has build issues and dependency problems that need fixing.

**Package**: `@nirholas/pump-agent-swarm` v0.1.0
**Chain**: Solana (mainnet-beta / devnet)
**Key deps**: `@solana/web3.js`, `@pump-fun/pump-sdk`, `bn.js`, `bs58`, `hono`, `pino`

## Current Issues

The package has a `postinstall` script that tries to compile the pump-sdk's TypeScript:
```json
"postinstall": "cd node_modules/@pump-fun/pump-sdk && npx tsc --declaration ..."
```

This is brittle. The build and type system need to be solid.

## Task

### 1. Fix Dependencies & Build

- Run `npm install` and fix any dependency resolution issues
- Ensure `@pump-fun/pump-sdk` installs correctly (if not published to npm, check if it's a git dependency or needs a local type declaration)
- Review `src/pump-sdk.d.ts` — this is the fallback type declaration. Make it comprehensive
- Fix all import paths throughout the codebase
- Ensure `npm run build` (`tsc -p tsconfig.build.json`) succeeds with zero errors

### 2. Fix TypeScript Types (`src/types.ts`)

Review and fix the complete type system:
- Ensure all types using `BN` (from bn.js) are properly imported
- Ensure `Keypair` imports from `@solana/web3.js` are correct
- Fix any circular dependency issues
- Add missing type exports to barrel files (`src/index.ts`, `src/agents/index.ts`, etc.)
- Ensure all 18 `SwarmPhase` states are properly typed
- Verify all 11 `AgentRole` types match actual agent implementations

### 3. Fix Barrel Exports

Each subdirectory has an `index.ts` barrel file. Verify all exports:
- `src/index.ts` — Main package entry
- `src/agents/index.ts` — All 10 agent types + MarketMakerAgent
- `src/trading/index.ts` — All trading engine modules
- `src/bundle/index.ts` — All bundle modules
- `

*[truncated — see source for full prompt]*