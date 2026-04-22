# HOLDER SYNCING

> The cron job now syncs top holders for each market alongside price history and market data.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Top Holders Syncing

The cron job now syncs top holders for each market alongside price history and market data.

## Overview

**Top holders** (also known as "whales") are the largest position holders in each Polymarket prediction market. Tracking these holders provides valuable insights into:

- Market sentiment from sophisticated traders
- Whale movements and position changes
- Social proof for market positions
- Smart money tracking

## What Gets Stored

For each market, we store the top holders with:

- **Address**: Wallet address of the holder
- **Username**: Polymarket username (if available)
- **Profile Image**: Avatar URL
- **Rank**: Position in the top holders list (1-10+ typically)
- **Outcome**: Which side they're betting on ("Yes" or "No")
- **Balance**: Number of shares held
- **Value**: USD value of their position
- **Updated At**: Timestamp of last sync

## Database Schema

```typescript
polymarketHolders {
  id: string (PK)
  marketId: string
  address: string
  userName: string | null
  profileImage: string | null
  rank: number
  outcome: string | null  // "Yes" or "No"
  balance: number
  value: number
  updatedAt: timestamp
}
```

## How It Works

### 1. Event ID Resolution

To fetch holders, we need the market's `eventId`:

```typescript
// Try to get from market data first
let eventId = market.events?.[0]?.id

// If not available, fetch market details
if (!eventId) {
  const details = await fetchMarketDetails(market.id)
  eventId = details.events?.[0]?.id
}
```

### 2. Dashboard API Call

We use the Polymarket Analytics dashboard API:

```typescript
const dashboard = await fetchMarketsDashboard(eventId)

// Dashboard includes:
// - holders: Array of top holder objects
// - charts: Market activity charts
// - volume: Trading volume data
```

### 3. Save to Database

```typescript
await saveHolders(marketId, dashboard.holders)

// This:
// 1. Clears existing holders for the market
// 2. Inserts new holders with rankings
// 3. Preserves holder m

*[truncated — see source for full prompt]*