# VIDEO 04 TREND FILTER CALMAN STRATEGY

> **Source:** YouTube (transcript provided by Captain 2026-03-07 07:22 UTC)  
**Agent:** the-great-cryptonio  
**Topic:** Trend-following indicator stra

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VIDEO 4: TradingView Trend Filter + Calman Trend Levels Strategy

**Source:** YouTube (transcript provided by Captain 2026-03-07 07:22 UTC)  
**Agent:** the-great-cryptonio  
**Topic:** Trend-following indicator strategy  
**Timeframe:** 15-minute (as demonstrated)  
**Assets:** Gold, BTC/ETH crypto  

---

## 📺 Video Intro

> "I've tested over 50 TradingView indicators and honestly most of them were complete garbage. But in the process, I discovered five absolute gamechangers that almost nobody is talking about."

**Focus:** Trend-based confluence strategy (2 of 5 indicators shown)

---

## 🔧 Indicator #1: Trend Filter

### How to Add:
1. Click **Indicators** tab in TradingView
2. Search: **"trend filter"**
3. Add to chart

### Settings:
| Parameter | Default | Modified | Purpose |
|-----------|---------|----------|---------|
| Length | 20 | **28** | Smoother trend detection |
| Style | Default | Hide some | Cleaner visuals |

### Signal Interpretation:
- **RED** two-pole filter line = **SELL** territory (downtrend)
- **GREEN** two-pole filter line = **BUY** territory (uptrend)

### Rule:
- Price **below** red line = Only take SELL trades
- Price **above** green line = Only take BUY trades

---

## 🔧 Indicator #2: Calman Trend Levels

### How to Add:
1. Click **Indicators** tab
2. Search: **"calman trend levels"**
3. Select by creator
4. Add to chart

### Settings:
| Parameter | Default | Modified | Purpose |
|-----------|---------|----------|---------|
| Short Length | 50 | **40** | Faster signal |
| Long Length | 150 | **80** | Responsive trend |

### Signal Output:
- **BUY signal box:** Price moves up
- **SELL signal box:** Price moves down

---

## 📊 Complete Trading Rules

### LONG Setup (BUY):
**ALL conditions must be met:**

1. ✅ Trend Filter shows **GREEN** two-pole filter line
2. ✅ Price moves **ABOVE** the green two-pole filter line
3. ✅ Calman Trend Levels gives **BUY** signal
4. ✅ **Confirmation:** **Bullish candle** present

**Entry:** Market ord

*[truncated — see source for full prompt]*