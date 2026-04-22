# TELEGRAM BOT

> > Crypto call tracking, leaderboards, PNL cards, and premium subscriptions via Telegram.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Telegram Bot (Crypto Vision)

> Crypto call tracking, leaderboards, PNL cards, and premium subscriptions via Telegram.

## Overview

Crypto Vision is a Telegram bot built with [Grammy](https://grammy.dev/) that enables crypto communities to track calls, maintain leaderboards, generate PNL cards, and manage premium features. It runs as a component of the root API service.

**Location:** `src/bot/`
**Framework:** Grammy (Telegram Bot Framework for TypeScript)
**Database:** PostgreSQL via Drizzle ORM
**Entry Point:** `src/bot/index.ts`

## Features

| Feature | Description |
|---------|-------------|
| **Call Tracking** | Track crypto trade calls with entry/target/stop-loss pricing |
| **Leaderboards** | Per-group leaderboards based on call accuracy and PNL |
| **PNL Cards** | Visual profit/loss cards generated with Sharp/Canvas |
| **Premium Subscriptions** | Paid premium tier with advanced features |
| **Referral System** | Referral tracking with rewards |
| **Hardcore Mode** | Challenge mode with stricter evaluation criteria |
| **Insider Alerts** | Real-time alerts for insider activity |
| **Group Management** | Multi-group support with per-group settings |
| **Channel Integration** | Channel-based call forwarding and broadcasting |

## Architecture

```
Telegram API
    │
    ▼
Grammy Bot (src/bot/telegram/bot.ts)
    │
    ├── Command Handlers
    │   ├── /start, /help
    │   ├── /call <token> <entry> <target> <sl>
    │   ├── /leaderboard
    │   ├── /pnl
    │   ├── /premium
    │   └── /hardcore
    │
    ├── Services
    │   ├── user-service       → User registration, profiles
    │   ├── group-service      → Group settings, permissions
    │   ├── call-service       → Call CRUD, evaluation
    │   ├── channel-service    → Channel management
    │   ├── leaderboard-service → Rankings, scoring
    │   ├── pnl-card           → Visual PNL card generation
    │   ├── premium-service    → Subscription management
    │   ├── referral-service   → Referral trackin

*[truncated — see source for full prompt]*