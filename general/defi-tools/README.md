# Defi Tools

> Practical DeFi utilities included in the toolkit.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# DeFi Tools Guide

Practical DeFi utilities included in the toolkit.

> **New to DeFi?** "DeFi" means Decentralized Finance — financial services run by code on blockchains instead of banks. See the [Glossary](GLOSSARY.md) for full definitions of DeFi terms like dust, slippage, bridge, and TVL.

---

## Dust Sweeper

**Location:** `defi-tools/sweep/`

### What Is "Dust"?

"Dust" refers to tiny token balances left in your wallet — often worth just cents or a few dollars each. Over time, you accumulate tokens from:
- Airdrops you forgot about
- Remainder of trades that didn't sell 100%
- Reward tokens from DeFi protocols
- Test transactions

Individually they're worthless, but combined they could be worth hundreds of dollars.

### What the Dust Sweeper Does

1. **Scans** your wallet across 8 chains for tokens below a threshold (e.g., $5)
2. **Identifies** which tokens have liquidity (can be sold)
3. **Batch swaps** them into a single asset (stablecoin or yield position)
4. **Bridges** assets cross-chain to a single destination via 6 bridge providers
5. **Reports** total recovered value

### Supported Chains

| Chain | Network ID | Status |
|-------|-----------|--------|
| BNB Smart Chain | 56 | ✅ |
| Ethereum | 1 | ✅ |
| Polygon | 137 | ✅ |
| Arbitrum | 42161 | ✅ |
| Base | 8453 | ✅ |
| Optimism | 10 | ✅ |
| Avalanche | 43114 | ✅ |
| Fantom | 250 | ✅ |

### Quick Start

```bash
cd defi-tools/sweep
bun install

# Scan for dust (read-only, safe)
bun run scan --wallet 0xYourAddress --chain bsc

# Sweep dust tokens into USDC
bun run sweep --wallet 0xYourAddress --chain bsc --target USDC
```

### API Server

The sweep tool includes a Hono-based REST API server with x402 micropayments:

```bash
cd defi-tools/sweep
bun run dev
# API available at http://localhost:3000
```

#### Key Endpoints

| Endpoint | Method | Cost (x402) | Description |
|----------|--------|-------------|-------------|
| `/api/wallet/:address/balances` | GET | Free | Get token balances across all chains 

*[truncated — see source for full prompt]*