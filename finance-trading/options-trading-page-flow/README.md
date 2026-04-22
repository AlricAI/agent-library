# OPTIONS TRADING PAGE FLOW

> This document describes how to build the **Option Trading** feature so it matches the reference UI: ETH/USDC funding rates, implied APR chart, order book (short/long rates), and order entry panel.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Option Trading Page — Implementation Flow

This document describes how to build the **Option Trading** feature so it matches the reference UI: ETH/USDC funding rates, implied APR chart, order book (short/long rates), and order entry panel.

---

## 1. Scope & Placement

| Item | Decision |
|------|----------|
| **Route** | `/options` — this is the main Option Trading feature. |
| **Navigation** | Existing "Options" in Trading sidebar → points to `/options`. |
| **Layout** | Full-width terminal: top bar → stats row → main area (chart | orderbook | order entry). |

---

## 2. Page Structure (Top → Bottom)

Build the page in this order so layout and data flow stay clear.

### Step 1: Top asset bar
- **Left:** Pair selector (e.g. ETHUSDC) with dropdown, star, info.
- **Right:** Maturity text, e.g. `25 days (Matures 27 Feb 2026)` with dropdown.
- **Data:** Symbol and maturity can be state; later from API (e.g. `/api/market-data` or options metadata).

### Step 2: Key metrics row
- One row, horizontal: **Implied APR**, **Mark APR**, **Underlying APR**, **Notional OI**, **24h Volume**, **Next Settlement** (countdown).
- **Data source:**  
  - Funding / APR: `GET /api/comprehensive/funding-rate/{symbol}/refresh` and `/funding-rate/{symbol}/analysis`.  
  - Map: `funding_rate` / `funding_rate_annualized` → Implied APR; add mock or separate endpoint for Mark APR, Underlying APR, OI, Volume, next funding time.
- **Updates:** Poll every 30–60s or use WebSocket later.

### Step 3: Main content (3 columns)
- **Left (≈50%):** Chart panel.  
- **Center (≈25%):** Order book.  
- **Right (≈25%):** Order entry.

### Step 4: Left panel — Chart
- **Tabs:** "APR Chart" (default), "My PnL".
- **APR Chart:** Timeframe buttons (5m, 1H, 1D, 1W). Small legend: Implied APR (OHLC-style), Underlying APR.
- **Chart:** Line chart: Implied APR and Underlying APR over time. Y-axis: percentage.
- **Data:** Historical funding/APR from `GET /api/comprehensive/funding-rate/{symbol}/analysis` (use hist

*[truncated — see source for full prompt]*