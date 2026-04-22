# What Is This

> A complete explanation for anyone — no tech background assumed.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# What Is This?

A complete explanation for anyone — no tech background assumed.

> **Already understand crypto and AI development?** You may want to skip to the [Architecture](architecture.md) guide or [Getting Started](getting-started.md) instead. This page is intentionally written for people who have never touched a blockchain or built anything with AI.

---

## The 30-Second Version

**BNB Chain AI Toolkit** is a free, open-source collection of tools that lets AI assistants (like Claude, ChatGPT, and others) interact with cryptocurrency and blockchain technology.

Think of it this way:

> Right now, if you ask Claude "What's the price of BNB?", it **guesses** based on old training data.
>
> With this toolkit, Claude can **actually look it up** — in real time, from the blockchain itself.

It goes much further than prices. The AI can check wallet balances, execute trades, analyze DeFi protocols, sweep leftover tokens, bridge assets between chains, and more.

---

## Why Does This Exist?

### The Problem (Before This Toolkit)

Imagine you want an AI to help you with crypto. Here's what that looks like today:

1. You open ChatGPT and ask "What's my wallet balance?"
2. The AI says "I can't access your wallet. Can you paste the data here?"
3. You go to a block explorer, copy the information, paste it back
4. The AI analyzes the static text you gave it
5. You need trading help? Open a different tool. Portfolio tracking? Another tool. News? Yet another.

Everything is **disconnected**. The AI is smart but blind — it can think about crypto but can't *see* or *touch* it.

### The Solution (With This Toolkit)

1. You open Claude and ask "What's my wallet balance?"
2. Claude calls the BNB Chain MCP server, which checks the blockchain directly
3. Claude says "Your wallet has 1.5 BNB ($930), 500 USDT, and 12 small tokens worth about $8 combined. Want me to sweep those dust tokens into USDC?"
4. You say yes, Claude executes the sweep
5. All within a single conversation — no sw

*[truncated — see source for full prompt]*