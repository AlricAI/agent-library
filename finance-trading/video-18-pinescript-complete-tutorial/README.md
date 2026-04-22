# VIDEO 18 PINESCRIPT COMPLETE TUTORIAL

> **Source:** YouTube Trading Education (transcript provided 2026-03-07 08:29 UTC)
**Status:** Advanced Pine Script + Strategy Development + Production 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VIDEO 18: Pine Script Tutorial — From Indicator to Strategy to Production

**Source:** YouTube Trading Education (transcript provided 2026-03-07 08:29 UTC)
**Status:** Advanced Pine Script + Strategy Development + Production Migration
**Difficulty:** Intermediate → Advanced
**Prerequisites:** Basic Pine Script (Video 17)

---

## 🎯 WHAT YOU'LL LEARN

1. ✅ Build indicators in Pine Script
2. ✅ Develop them into **backtestable strategies**
3. ✅ Optimize for market conditions
4. ✅ **Migrate to production** via exchange APIs

---

## 📍 PART 1: TradingView Setup

### Choose Your Market
**Recommendation:** Use what you know best
- **Forex:** EUR/USD
- **Stocks:** Your familiar ticker
- **Crypto:** BTC/USD (used in tutorial, 1H timeframe)

**Timeframe:** 1H for detail (tutorial uses 1H)

---

## 📝 PART 2: First Pine Script Indicator

### Basic Moving Average Indicator

```pinescript
//@version=5
indicator("My MA Indicator", overlay=true)

// Overlay = true → draws on price chart (not below)

// Define moving averages
fastMA = ta.sma(close, 24)   // Simple MA, 24 periods, close price
slowMA = ta.sma(close, 200)  // Simple MA, 200 periods

// Plot them
plot(fastMA, "Fast MA", color=color.blue)
plot(slowMA, "Slow MA", color=color.yellow)
```

**What is `overlay=true`?**
- `true` = Plots **on** the price chart
- `false` = Plots in **separate panel** below

---

## 📊 PART 3: Pine Script Fundamentals

### Series Data Concept

**TradingView builds around "series data":**

| Variable | Description |
|----------|-------------|
| `open` | Opening price of period |
| `high` | Highest price of period |
| `low` | Lowest price of period |
| `close` | Closing price of period |
| `volume` | Trading volume |
| `time` | Timestamp |

**Execution Model:**
- Script executes **on every candle**
- For 100 candles → script runs 100 times
- Calculates from start to end of each period

### Built-in Functions

**Technical Analysis Functions:**
```pinescript
// RSI (Relative Strength Index)
rsiV

*[truncated — see source for full prompt]*