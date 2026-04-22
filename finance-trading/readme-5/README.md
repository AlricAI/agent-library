# README

> Production-ready AI agent templates for cryptocurrency news and trading applications.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🤖 AI Agent Templates

Production-ready AI agent templates for cryptocurrency news and trading applications. Built with LangChain and designed for real-world deployment.

## Available Agents

| Agent | Description | Key Features |
|-------|-------------|--------------|
| [Trading Bot](trading-bot.py) | AI-powered trading signal generator | Multi-strategy, sentiment analysis, LangChain tools |
| [Research Assistant](research-assistant.py) | Deep-dive crypto research with citations | Multi-depth research, follow-up Q&A, report generation |
| [Alert Bot](alert-bot.py) | Real-time news alerts | Telegram/Discord/Slack, keyword filters, whale tracking |
| [Digest Bot](digest-bot.py) | Scheduled AI news digests | Email/Slack delivery, HTML templates, scheduling |
| [Sentiment Tracker](sentiment-tracker.py) | Live sentiment dashboard | VADER+LLM hybrid, terminal charts, trend detection |

## Quick Start

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Set your API keys
export OPENAI_API_KEY="sk-..."
export ANTHROPIC_API_KEY="sk-ant-..."

# 3. Run any agent!
```

### Trading Bot

```bash
# Generate trading signals for Bitcoin
python trading-bot.py --coin btc --strategy moderate

# Scan top 10 coins for opportunities
python trading-bot.py --scan --limit 10

# Output: trading_signals.json
```

### Research Assistant

```bash
# Interactive mode
python research-assistant.py

# Single query
python research-assistant.py --query "What's happening with Ethereum L2s?"

# Generate full report
python research-assistant.py --query "DeFi trends" --report --depth deep
```

### Alert Bot

```bash
# Keyword alerts to Telegram
python alert-bot.py --keywords "bitcoin,regulation" --channel telegram

# Breaking news only to Discord
python alert-bot.py --breaking --channel discord

# Whale movement alerts
python alert-bot.py --whales --min-amount 10000000 --channel slack

# Console testing (no setup required)
python alert-bot.py --keywords "bitcoin" --channel console
``

*[truncated — see source for full prompt]*