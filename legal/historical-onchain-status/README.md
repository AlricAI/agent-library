# HISTORICAL ONCHAIN STATUS

> Last updated: 2026-03-30

## Current Doctrine Warning

- This file documents a **historical on-chain contract state**
- It does **not** override the c

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# HISTORICAL ON-CHAIN STATUS

Last updated: 2026-03-30

## Current Doctrine Warning

- This file documents a **historical on-chain contract state**
- It does **not** override the current founder-directed conservative **10% charitable cap** for LLC operations
- Do not use this file by itself to justify live `60/30/10`, `100% charity`, or named-beneficiary claims in public or customer-facing copy

## Verified Live Base State

- Live verified split contract: `GospelDonation.sol`
- Live verified Base address: `0x9855B75061D4c841791382998f0CE8B2BCC965A4`
- BaseScan confirms internal split payouts from that contract to:
  - Charity `60%`: `0x8d3dEADbE2b4B857A43331D459270B5eedC7084e`
  - Infrastructure treasury `30%`: `0xe0a42f83900af719019eBeD3D9473BE8E8f2920b`
  - Founder ops `10%`: `0x7c3E283119718395Ef5EfBAC4F52738C2018daA7`

This is the current live on-chain truth for the historical contract deployment.

## Verified Live Again — 2026-03-13 18:13 ET

Codex re-verified the live Base state on 2026-03-13 using:
- official Base Mainnet RPC `eth_getCode` against `0x9855B75061D4c841791382998f0CE8B2BCC965A4`, which returned non-empty runtime bytecode
- BaseScan verified source and live internal transaction history for the same contract:
  - [Contract address](https://basescan.org/address/0x9855B75061D4c841791382998f0CE8B2BCC965A4)
  - [Observed split tx example 1](https://basescan.org/tx/0x237c7ecf50f6e3a0fe6946f2f7533f291f9ad491d35c9c89e85bf8a13ae97301)
  - [Observed split tx example 2](https://basescan.org/tx/0x57a812f7d14935f5d9d6c6071f1790d161fe550a6397817e45098fe0003050dc)

What was confirmed:
- the contract is live on Base Mainnet, not an undeployed placeholder
- the verified source still hardcodes the same three payout destinations
- the observed ETH internal transfers still match the `60/30/10` pattern:
  - `0.00006 ETH` to `0x8d3d...` (60%)
  - `0.00003 ETH` to `0xe0a42...` (30%)
  - `0.00001 ETH` to `0x7c3E...` (10%)

Inference:
- Grok's "vaporware" concern is not s

*[truncated — see source for full prompt]*