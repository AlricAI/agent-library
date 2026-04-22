# Standards

> Open standards for AI agents and Web3 accessibility — both proposed by this project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Standards Guide

Open standards for AI agents and Web3 accessibility — both proposed by this project.

> **New to standards?** Think of standards as shared rule books that everyone agrees to follow. ERC-8004 is like a phone directory for AI agents on the blockchain. W3AG is like building codes that ensure buildings are wheelchair-accessible — but for crypto apps. See the [Glossary](GLOSSARY.md) for term definitions.

---

## ERC-8004: Agent Discovery & Trust

**Location:** `standards/erc-8004/`

### What Is It?

ERC-8004 is an Ethereum standard (EIP) for on-chain AI agent discovery and trust. It defines a smart contract protocol that lets AI agents:

1. **Register** themselves on the blockchain
2. **Discover** other agents
3. **Build reputation** through verified interactions
4. **Establish trust** without centralized authorities

### Why Does It Matter?

Right now, if you want to use an AI agent, you have to trust the developer who made it. There's no way to verify:
- Is this agent legitimate?
- Has it performed well in the past?
- Can other agents vouch for it?

ERC-8004 solves this by putting agent registration and reputation on-chain — transparent, immutable, and verifiable by anyone.

### How It Works

```
Agent Developer
       │
       ▼
  Register Agent (on-chain)
       │
       ▼
  Agent Registry Contract
       │
       ├── Agent metadata (name, capabilities, version)
       ├── Reputation score
       ├── Verification status
       └── Trust attestations from other agents
       │
       ▼
  Anyone can discover and verify agents
```

### Smart Contracts

Located in `standards/erc-8004/contracts/`:

| Contract | Description |
|----------|-------------|
| `IdentityRegistryUpgradeable.sol` | Main registry for agent registration |
| `ReputationRegistryUpgradeable.sol` | Trust attestation and reputation |
| `ValidationRegistryUpgradeable.sol` | Validation and attestation registry |

**Deployed on:**
- BSC Mainnet & Testnet
- opBNB Mainnet & Testnet
- Ethere

*[truncated — see source for full prompt]*