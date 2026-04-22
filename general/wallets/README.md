# Wallets

> Offline-capable wallet operations for BNB Chain and EVM networks.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Wallets Guide

Offline-capable wallet operations for BNB Chain and EVM networks.

> **New to crypto wallets?** A wallet is software that holds the keys to your crypto accounts. The wallet doesn't hold your coins — the blockchain does. The wallet holds the *keys* that prove ownership. See the [Glossary](GLOSSARY.md) for definitions of wallet, private key, seed phrase, and other terms.

---

## Ethereum Wallet Toolkit

**Location:** `wallets/ethereum-wallet-toolkit/`

A complete wallet utility that works offline. Fully compatible with BNB Smart Chain (BSC) and all EVM chains.

### Features

| Feature | Description | Needs Internet? |
|---------|-------------|:--------------:|
| HD Wallet Generation | Create wallets from seed phrases (BIP-39/44) | ❌ |
| Vanity Addresses | Generate addresses with custom prefixes | ❌ |
| Message Signing | Sign messages (EIP-191, EIP-712) | ❌ |
| Transaction Signing | Sign transactions (legacy + EIP-1559) | ❌ |
| Keystore Files | Import/export Keystore V3 format | ❌ |
| Balance Checking | Check token balances | ✅ |
| Transaction Broadcasting | Send signed transactions | ✅ |

### Quick Start

```bash
cd wallets/ethereum-wallet-toolkit
bun install
```

### Generate a New Wallet

```typescript
import { generateWallet } from '@nirholas/wallet-toolkit';

const wallet = generateWallet();
console.log('Address:', wallet.address);
console.log('Mnemonic:', wallet.mnemonic);
// ⚠️ Store the mnemonic securely! Anyone with it controls your funds.
```

### Sign a Transaction (Offline)

```typescript
import { signTransaction } from '@nirholas/wallet-toolkit';

const signedTx = signTransaction({
  to: '0xRecipientAddress',
  value: '1000000000000000000', // 1 BNB in wei
  chainId: 56, // BSC mainnet
  gasLimit: 21000,
  gasPrice: '5000000000', // 5 Gwei
}, privateKey);

// Broadcast later when online
```

### MCP Server Integration

The wallet toolkit includes specialized MCP servers:

```json
{
  "mcpServers": {
    "wallet": {
      "command": "node"

*[truncated — see source for full prompt]*