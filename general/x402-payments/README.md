# X402 PAYMENTS

> > HTTP 402 micropayment system for pay-per-request API access.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# x402 Payments

> HTTP 402 micropayment system for pay-per-request API access.

## Overview

Crypto Vision implements [x402](https://www.x402.org/) — Coinbase's HTTP 402 payment protocol — to enable agents and users to pay for premium API endpoints with USDC stablecoin. Instead of traditional API key subscriptions, clients pay per request using on-chain micropayments.

This enables a new paradigm: **give your agent a wallet with USDC, and it can autonomously purchase premium intelligence data**.

## How x402 Works

The x402 protocol adds a payment layer to standard HTTP:

```
┌──────────┐                    ┌──────────────┐                  ┌─────────────┐
│  Client   │ ──── GET /api ──► │  API Server   │                  │ Facilitator │
│  (Agent)  │ ◄── 402 + reqs ── │              │                  │ (x402.org)  │
│           │                    │              │                  │             │
│  Sign     │                    │              │                  │             │
│  EIP-3009 │                    │              │                  │             │
│           │ ── GET + X-PAY ──► │  Verify ─────────────────────► │  Settle     │
│           │ ◄── 200 + data ── │              │ ◄── tx hash ──── │  on-chain   │
└──────────┘                    └──────────────┘                  └─────────────┘
```

### Step-by-Step Flow

1. **Client requests a premium endpoint** (no payment attached)
2. **Server returns HTTP 402** with payment requirements in the `X-PAYMENT-REQUIRED` header (base64-encoded JSON)
3. **Client parses requirements** — learns the price, payment address, network, and asset
4. **Client signs an EIP-3009 `transferWithAuthorization`** — USDC gasless transfer authorization
5. **Client retries with `X-PAYMENT` header** containing the signed payment proof (base64-encoded)
6. **Server forwards to facilitator** — the facilitator validates the signature and settles on-chain
7. **Server returns data** with `X-Payment-Response` header containing the settl

*[truncated — see source for full prompt]*