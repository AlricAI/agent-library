# 02 Dashboard Market Pages

> ## Context

You are working on `crypto-vision`, a cryptocurrency intelligence platform. The dashboard is in `apps/dashboard/` (Next.js 15, Tailwind CS

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 02 — Dashboard Market Data Pages

## Context

You are working on `crypto-vision`, a cryptocurrency intelligence platform. The dashboard is in `apps/dashboard/` (Next.js 15, Tailwind CSS, App Router). The design system from Prompt 01 gives you a dark trading-terminal aesthetic with sidebar navigation.

The backend API runs at `http://localhost:8080` with 200+ endpoints. The dashboard's `src/lib/market-data.ts` already has full CoinGecko integration with caching and rate limiting.

## Existing Code to Keep

- `apps/dashboard/src/lib/market-data.ts` — All market data fetching functions (getTopCoins, getTrending, getGlobalMarketData, getFearGreedIndex, etc.)
- `apps/dashboard/src/lib/analytics.ts` — Correlation, volatility analysis
- `apps/dashboard/src/lib/defi.ts` — DeFi protocol data
- `apps/dashboard/src/app/coin/` — Individual coin pages
- All API integration code in `src/lib/`

## Task

### 1. Redesign the Home Page (`src/app/page.tsx`)

Replace the CoinGecko-style home page with a **trading dashboard overview**:

**Top Row — Global Stats Strip:**
- Total Market Cap (with 24h change %)
- 24h Volume
- BTC Dominance (mini donut chart)
- ETH Gas (gwei, color-coded)
- Fear & Greed Index (gauge visualization)
- All using `AnimatedNumber` component with real data from `getGlobalMarketData()`

**Main Grid (3 columns on desktop):**

Column 1 (wide):
- **Price Ticker Table** — Top 50 coins, compact rows:
  - Rank, Logo, Name/Symbol, Price (animated), 1h/24h/7d change (color-coded), Sparkline (7d), Volume bar, Market cap
  - Sortable headers, click to navigate to `/coin/[id]`
  - Use existing `getTopCoins()` data

Column 2 (medium):
- **Trending Now** — Top 10 trending with mini price charts
- **Top Gainers** — 24h gainers with % badges
- **Top Losers** — 24h losers

Column 3 (narrow):
- **Market Mood** — Fear & Greed gauge (redesigned, not the current widget)
- **BTC Dominance** — Donut chart
- **Gas Tracker** — Multi-chain gas prices
- **Quick Stats** — Active cr

*[truncated — see source for full prompt]*