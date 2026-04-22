# Agents

> Everything you need to know about the 78 AI agents — what they are, how to use them, and how to create your own.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Agents Guide

Everything you need to know about the 78 AI agents — what they are, how to use them, and how to create your own.

> **New here?** An AI agent is just a set of instructions (a "personality") that makes a general-purpose AI act like a domain expert. No coding required to use them. See the [Glossary](GLOSSARY.md) for term definitions.

---

## What Are AI Agents?

AI agents are pre-configured personality definitions for AI assistants. Each agent is a JSON file that contains:

- **A specific role** — What it specializes in (trading, analysis, staking, etc.)
- **System prompt** — Instructions that shape how the AI behaves and what it knows
- **Tool access** — Which MCP tools it can use for real-time data
- **Knowledge** — Domain-specific context and expertise
- **Opening questions** — Suggested first questions to ask the agent

You load an agent into your AI assistant (Claude, ChatGPT, etc.), and it becomes a specialist in that domain.

**Analogy:** Loading an agent is like handing an expert a role card before a conversation. The expert (your AI) reads the card and acts accordingly — bringing the right knowledge, using the right tools, and giving domain-specific answers.

### What Agents Can NOT Do

- Agents don't *run* code — they're inert JSON text
- Agents don't access your wallet or keys — they need an MCP server for that
- Agents aren't magic — they improve AI accuracy in their domain but don't guarantee correct answers
- Agents don't learn between sessions — each conversation starts fresh

---

## Find the Right Agent for Your Task

Not sure which agent to use? Start with your goal:

| I Want To... | Best Agent(s) | Category |
|-------------|---------------|----------|
| Trade tokens on PancakeSwap | PancakeSwap Trader | BNB Chain |
| Earn interest on my crypto | Venus Protocol Expert, Binance Earn Specialist | BNB Chain |
| Stake BNB for rewards | BNB Staking Advisor, BNB Liquid Staking | BNB Chain |
| Check if a token is safe | BSC Smart Contra

*[truncated — see source for full prompt]*