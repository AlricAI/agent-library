# DATABASE

> > PostgreSQL schema (Drizzle ORM) and BigQuery data warehouse tables for Crypto Vision.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Database

> PostgreSQL schema (Drizzle ORM) and BigQuery data warehouse tables for Crypto Vision.

## Overview

Crypto Vision uses two database systems:

| System | Purpose | Required |
|---|---|---|
| **PostgreSQL 16** | Telegram bot data (users, groups, calls, subscriptions) | Required for bot features |
| **BigQuery** | Time-series data warehouse (market snapshots, DeFi, news) | Required for data pipeline |

Both are optional for the core API — the API works without either by fetching directly from upstream sources.

---

## PostgreSQL Schema

### Connection

```
DATABASE_URL=postgresql://cryptovision:cryptovision@localhost:5432/cryptovision
```

Schema is managed via **Drizzle ORM** (`drizzle.config.ts`). Migrations live in `src/bot/db/migrations/`.

### Enums

| Enum | Values | Used In |
|---|---|---|
| `call_type` | `alpha`, `gamble` | calls |
| `call_mode` | `auto`, `button` | groups |
| `display_mode` | `simple`, `advanced` | groups |
| `rank_tier` | `amateur`, `rookie`, `trader`, `expert`, `whale`, `oracle` | users |
| `channel_permission` | `owner`, `owner_admins`, `everyone` | call_channels |
| `ad_type` | `button_24h`, `button_72h`, `button_1w`, `broadcast` | advertisements |
| `ad_status` | `pending`, `active`, `expired`, `cancelled` | advertisements |
| `chain` | `ethereum`, `solana`, `base`, `bsc`, `arbitrum`, `polygon`, `avalanche`, `optimism` | calls |
| `referral_status` | `pending`, `approved`, `rejected` | referrals |
| `subscription_status` | `active`, `expired`, `cancelled` | premium_subscriptions |
| `language` | `en`, `zh`, `de`, `ru`, `vi`, `pl`, `pt`, `ar` | users, groups |

### Tables

#### `users`

User profiles for the Telegram bot.

| Column | Type | Notes |
|---|---|---|
| `id` | uuid | PK, auto-generated |
| `telegram_id` | varchar(50) | Unique, not null |
| `username` | varchar(100) | Nullable |
| `wallet_addresses` | jsonb | `[]` default |
| `total_calls` | integer | Default 0 |
| `total_wins` | integer | Default 0 |
| `performanc

*[truncated — see source for full prompt]*