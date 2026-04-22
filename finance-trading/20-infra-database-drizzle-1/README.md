# 20 Infra Database Drizzle

> ## Context

You are working on the database layer of crypto-vision. The project uses:

- **PostgreSQL 16** as the primary database
- **Drizzle ORM** v

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 20 — Infrastructure: Database Schema, Migrations & Drizzle ORM

## Context

You are working on the database layer of crypto-vision. The project uses:

- **PostgreSQL 16** as the primary database
- **Drizzle ORM** v0.45 for schema management and queries
- `drizzle.config.ts` — Drizzle Kit config at project root
- `src/lib/db/` — Database connection and schema
- `src/bot/db/` — Bot-specific schema (Telegram bot)

The API server needs PostgreSQL for:
- API key storage and management
- User data (for premium features)
- Portfolio data (server-side sync)
- Cached market data snapshots
- Anomaly detection results
- Search analytics
- Agent execution logs

The Telegram bot needs tables for:
- Users, groups, channels
- Token calls and PnL tracking
- Premium subscriptions
- Referral system
- Leaderboard data

## Task

### 1. Complete the Core Schema (`src/lib/db/schema.ts`)

Define all tables using Drizzle ORM:

```typescript
import { pgTable, text, integer, timestamp, real, jsonb, boolean, serial, uuid, index, uniqueIndex } from 'drizzle-orm/pg-core';

// API Keys
export const apiKeys = pgTable('api_keys', {
  id: uuid('id').defaultRandom().primaryKey(),
  name: text('name').notNull(),
  keyHash: text('key_hash').notNull().unique(),
  keyPrefix: text('key_prefix').notNull(), // First 8 chars for identification
  tier: text('tier', { enum: ['free', 'pro', 'enterprise'] }).default('free').notNull(),
  rateLimit: integer('rate_limit').default(100).notNull(), // requests per minute
  requestCount: integer('request_count').default(0).notNull(),
  lastUsedAt: timestamp('last_used_at'),
  expiresAt: timestamp('expires_at'),
  isActive: boolean('is_active').default(true).notNull(),
  metadata: jsonb('metadata'),
  createdAt: timestamp('created_at').defaultNow().notNull(),
  updatedAt: timestamp('updated_at').defaultNow().notNull(),
}, (table) => ({
  keyHashIdx: uniqueIndex('api_keys_key_hash_idx').on(table.keyHash),
  prefixIdx: index('api_keys_prefix_idx').on(table.keyPr

*[truncated — see source for full prompt]*