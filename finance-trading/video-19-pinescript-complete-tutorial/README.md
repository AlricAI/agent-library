# VIDEO 19 PINESCRIPT COMPLETE TUTORIAL

> **Source:** YouTube Trading Education (transcript provided 2026-03-07 08:31 UTC)
**Status:** Pine Script Comprehensive Tutorial
**Difficulty:** Beginn

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VIDEO 19: Complete Pine Script Tutorial — From Basics to Backtesting

**Source:** YouTube Trading Education (transcript provided 2026-03-07 08:31 UTC)
**Status:** Pine Script Comprehensive Tutorial
**Difficulty:** Beginner → Intermediate
**Prerequisites:** None (starts from basics)

---

## 🎯 WHAT YOU'LL BUILD

A complete **trend-following strategy** with:
- Moving Average crossover signals
- Buy/Sell indicators on chart
- Backtesting with Strategy Tester
- User-configurable inputs (stop loss, take profit)
- Risk management

---

## 📍 PART 1: Getting Started

### Access TradingView
1. Go to **tradingview.com**
2. Open your desired chart
3. Click **"Pine Editor"** at bottom of screen

**What is Pine Editor?**
- The IDE where you write Pine Script code
- Code written here shows output on the chart
- Console shows errors and indicator states

---

## 📝 PART 2: Your First Indicator

### Basic Template

```pinescript
//@version=5
indicator("My First Indicator", overlay=true)
```

**Line-by-line breakdown:**

| Line | Code | Meaning |
|------|------|---------|
| 1 | `//@version=5` | **Version 5** (newest). Always use v5. |
| 2-3 | `// comments` | **Comments** — gray text, ignored by compiler |
| 4 | `indicator(...)` | **Title** of your indicator |
| 5 | `overlay=true` | **Draw on price chart** (false = separate panel) |

**Comments syntax:**
```pinescript
// Everything after slashes is ignored
// Use for notes and documentation
```

---

## 📊 PART 3: Coding a Moving Average

### SMA (Simple Moving Average)

```pinescript
//@version=5
indicator("Moving Average Example", overlay=true)

// Define the MA
ma1 = ta.sma(close, 200)  // 200-period SMA of closing prices

// Plot it on chart
plot(ma1)
```

**Breaking it down:**

| Component | Explanation |
|-----------|-------------|
| `ma1` | **Variable name** — can be anything (ma1, myMA, fastMA, etc.) |
| `=` | **Assignment** — gives the variable a value |
| `ta.sma()` | **Simple Moving Average function** |
| `close` | **D

*[truncated — see source for full prompt]*