# ICP COMPLETE GUIDE

> ## Performance Supply Depot LLC - Web3 Knowledge Base

---

## Table of Contents
1. [ICP Fundamentals](#1-icp-fundamentals)
2. [Motoko Programming](#2

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# The Great Cryptonio's Complete ICP Guide
## Performance Supply Depot LLC - Web3 Knowledge Base

---

## Table of Contents
1. [ICP Fundamentals](#1-icp-fundamentals)
2. [Motoko Programming](#2-motoko-programming)
3. [Canister Development](#3-canister-development)
4. [Web3 Integration](#4-web3-integration)
5. [Deployment Guide](#5-deployment-guide)
6. [Code Examples](#6-code-examples)

---

## 1. ICP Fundamentals

### What is the Internet Computer?

The Internet Computer (IC) is a decentralized cloud computing platform that extends the internet's functionality with serverless cloud capabilities. It's a blockchain that runs at web speed with infinite capacity.

### Core Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    INTERNET COMPUTER                         │
├─────────────────────────────────────────────────────────────┤
│  ┌──────────┐  ┌──────────┐  ┌──────────┐                  │
│  │ Subnet 1 │  │ Subnet 2 │  │ Subnet N │   ...             │
│  │ • Nodes  │  │ • Nodes  │  │ • Nodes  │                  │
│  │ • Canist │  │ • Canist │  │ • Canist │                  │
│  └──────────┘  └──────────┘  └──────────┘                  │
│                                                              │
│  Chain Key Cryptography - Single 48-byte public key         │
│  for the entire network                                      │
└─────────────────────────────────────────────────────────────┘
```

### Key Components

#### Canisters
- **Definition:** Smart contracts evolved - they contain both code AND state
- **Capacity:** Up to 4GB of memory per canister
- **Cost:** Pay for computation with cycles (1 trillion cycles ≈ $1.30)
- **Capabilities:** 
  - Serve web content directly (no traditional servers needed!)
  - Store and process data
  - Call other canisters
  - Make HTTP requests to the outside world

#### Subnets
- Blockchain partitions running on dedicated node machines
- Each subnet can host thousands of canisters

*[truncated — see source for full prompt]*