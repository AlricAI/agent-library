# 04 Dashboard Portfolio Watchlist

> ## Context

You are working on `crypto-vision` dashboard (`apps/dashboard/`, Next.js 15). The app already has full implementations for portfolio track

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 04 — Dashboard Portfolio, Watchlist & Alerts

## Context

You are working on `crypto-vision` dashboard (`apps/dashboard/`, Next.js 15). The app already has full implementations for portfolio tracking, watchlist management, and price alerts in the lib layer:

- `apps/dashboard/src/lib/portfolio.ts` — Portfolio tracking with localStorage
- `apps/dashboard/src/lib/watchlist.ts` — Watchlist management
- `apps/dashboard/src/lib/alerts.ts` — Price alert system
- `apps/dashboard/src/components/portfolio/` — Existing portfolio components
- `apps/dashboard/src/components/watchlist/` — Existing watchlist components
- `apps/dashboard/src/components/alerts/` — Alert modal and list components
- Providers: `PortfolioProvider`, `WatchlistProvider`, `AlertsProvider`

## Task

### 1. Redesign Portfolio Page (`/portfolio`)

Replace the existing portfolio page with a professional portfolio tracker:

**Portfolio Summary Header:**
- Total value (large, animated number)
- 24h P&L (absolute + percentage, color-coded)
- All-time P&L
- Best/worst performer badges

**Holdings Table:**
- Columns: Asset (logo + name), Amount, Avg Buy Price, Current Price, Value, P&L ($ + %), Allocation %
- Sortable by any column
- Click row → coin detail page
- Inline sparkline (7d) per row
- Color-coded P&L cells

**Allocation Chart:**
- Donut chart showing portfolio allocation by coin
- Toggle between: by value, by sector, by chain
- "Others" bucket for small holdings

**Performance Chart:**
- Portfolio value over time (line chart)
- Time range: 24h, 7d, 30d, 90d, 1y, All
- Overlay: individual assets vs total
- Benchmark comparison: vs BTC, vs ETH, vs S&P 500

**Transaction History:**
- Add transaction button (buy/sell/transfer)
- Transaction form: coin search, amount, price, date, fee, notes
- Transaction list with filters
- Import from CSV

### 2. Redesign Watchlist Page (`/watchlist`)

**Watchlist Grid:**
- Multiple watchlists (tabs): "Main", "DeFi Picks", "Memes", etc.
- Create/rename/delete wat

*[truncated — see source for full prompt]*