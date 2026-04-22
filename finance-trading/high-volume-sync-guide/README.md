# HIGH VOLUME SYNC GUIDE

> ## Overview

A complete solution for scraping all active Polymarket prediction markets with volume above a threshold (default: $100k) and storing thei

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# High-Volume Markets Sync Guide

## Overview

A complete solution for scraping all active Polymarket prediction markets with volume above a threshold (default: $100k) and storing their historical price data in your database.

## What Was Built

### 1. API Endpoint
**Location:** `app/api/polymarket/markets/sync-high-volume/route.ts`

- POST endpoint that accepts `minVolume` and `interval` parameters
- Fetches all active markets from Polymarket
- Filters by 24-hour volume
- Saves market metadata and historical price data
- Returns detailed statistics about the sync

### 2. CLI Script
**Location:** `scripts/sync-high-volume-markets.ts`

- Convenient command-line interface for running the sync
- Accepts command-line arguments for minVolume and interval
- Provides colorful output with progress updates
- Handles errors gracefully

### 3. NPM Script
**Added to:** `package.json`

```json
"sync:high-volume-markets": "tsx scripts/sync-high-volume-markets.ts"
```

### 4. Bug Fixes
**Fixed in:** `packages/investing/src/prediction/polymarket.ts`

- Fixed `saveMarkets` function that was trying to `JSON.parse()` arrays
- Changed lines 644-645 and 665-666 from `JSON.parse()` to `JSON.stringify()`

## Quick Start

### Option 1: Using NPM Script (Easiest)

```bash
# Sync markets with volume >= $100k (default)
npm run sync:high-volume-markets

# Custom volume threshold
npm run sync:high-volume-markets 200000

# Custom volume and interval
npm run sync:high-volume-markets 150000 1d
```

### Option 2: Using API Endpoint (Programmatic)

```bash
# Using curl
curl -X POST http://localhost:3000/api/polymarket/markets/sync-high-volume \
  -H "Content-Type: application/json" \
  -d '{"minVolume": 100000, "interval": "1h"}'

# Or from your app
fetch('/api/polymarket/markets/sync-high-volume', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ minVolume: 100000, interval: '1h' })
})
```

### Option 3: Direct Script Execution

```bash
npx tsx scripts/

*[truncated — see source for full prompt]*