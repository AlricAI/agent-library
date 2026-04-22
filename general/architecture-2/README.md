# Architecture

> How everything in the BNB Chain AI Toolkit fits together — and *why* it's designed this way.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Architecture

How everything in the BNB Chain AI Toolkit fits together — and *why* it's designed this way.

> **New to this project?** Start with [What Is This?](what-is-this.md) for a non-technical overview, or the [Glossary](GLOSSARY.md) if you encounter unfamiliar terms.

---

## The Big Picture

The toolkit is a **monorepo** (one repository containing many independent projects) with six main component groups. Each group can be used independently, but they're designed to work together.

```
┌──────────────────────────────────────────────────────────────┐
│                     BNB Chain AI Toolkit                      │
├──────────────┬──────────────┬──────────────┬─────────────────┤
│   AI Agents  │ MCP Servers  │  Market Data │   DeFi Tools    │
│   (78)       │   (6)        │  (2)         │   + Wallets     │
│              │              │              │   + Standards    │
│  BNB Chain   │  bnbchain    │  prices      │   sweep         │
│  agents (36) │  binance     │  news        │   wallet-tk     │
│  DeFi        │  binance-us  │  sentiment   │   ERC-8004      │
│  agents (42) │  universal   │              │   W3AG          │
│              │  agenti      │              │                 │
│              │  ucai        │              │                 │
└──────┬───────┴──────┬───────┴──────┬───────┴────────┬────────┘
       │              │              │                │
       ▼              ▼              ▼                ▼
   Claude/GPT    Blockchains     CoinGecko      Smart Contracts
   Copilot       BSC, opBNB      DeFiLlama      on BSC/Ethereum
   Any LLM        chains      200+ sources
```

**How to read this diagram:** The top box is the toolkit. Each column is a component group. The bottom row shows what each group connects to in the outside world.

---

## Why a Monorepo?

We chose a monorepo over separate repositories because:

| Benefit | Why It Matters |
|---------|---------------|
| **Single clone** | One `git clone` gives you everything. No

*[truncated — see source for full prompt]*