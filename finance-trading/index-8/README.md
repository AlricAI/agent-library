# Index

> API documentation for AI agents and autonomous trading packages

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agents API Reference

Agent packages enable AI-powered autonomous trading and on-chain operations.

## Packages

| Package | Description |
|---------|-------------|
| `@nirholas/agent-wallet` | CDP-based agent wallets |
| `@nirholas/agents-ai` | AI agent framework |
| `@nirholas/agents-autonomous` | Autonomous trading agents |
| `@nirholas/agents-plugins` | Agent plugin system |

---

## Agent Wallet (CDP)

The Agent Wallet package provides Coinbase Developer Platform (CDP) integration for AI agents.

### Installation

```bash
pnpm add @nirholas/agent-wallet
```

### Configuration

```typescript
import { AgentWallet } from '@nirholas/agent-wallet'

const wallet = new AgentWallet({
  cdpApiKeyName: process.env.CDP_API_KEY_NAME!,
  cdpApiKeyPrivate: process.env.CDP_API_KEY_PRIVATE!,
  network: 'base-mainnet', // or 'base-sepolia' for testnet
})
```

### Wallet Management

#### createWallet

Create a new agent wallet.

```typescript
async function createWallet(options?: CreateWalletOptions): Promise<Wallet>

interface CreateWalletOptions {
  name?: string
  network?: NetworkId
}

interface Wallet {
  id: string
  address: string
  network: NetworkId
  createdAt: Date
}

type NetworkId = 
  | 'base-mainnet'
  | 'base-sepolia'
  | 'ethereum-mainnet'
  | 'ethereum-sepolia'
  | 'polygon-mainnet'
  | 'arbitrum-mainnet'
```

**Example:**

```typescript
const wallet = await agentWallet.createWallet({
  name: 'trading-agent-1',
  network: 'base-mainnet',
})
console.log(`Created wallet: ${wallet.address}`)
```

#### getWallet

Get wallet by ID.

```typescript
async function getWallet(walletId: string): Promise<Wallet>
```

#### listWallets

List all wallets.

```typescript
async function listWallets(): Promise<Wallet[]>
```

#### exportWallet

Export wallet for backup.

```typescript
async function exportWallet(walletId: string): Promise<ExportedWallet>

interface ExportedWallet {
  walletId: string
  seed: string
  networkId: string
}
```

#### importWallet

Import a previou

*[truncated — see source for full prompt]*