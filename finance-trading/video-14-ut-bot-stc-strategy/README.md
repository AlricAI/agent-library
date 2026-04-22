# VIDEO 14 UT BOT STC STRATEGY

> **Source:** YouTube Trading Tutorial (transcript provided 2026-03-07 08:05 UTC)
**Status:** Strategy Summary Complete
**Instrument:** Forex/Crypto (5M

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VIDEO 14: UT Bot Alert + STC Oscillator Scalping Strategy

**Source:** YouTube Trading Tutorial (transcript provided 2026-03-07 08:05 UTC)
**Status:** Strategy Summary Complete
**Instrument:** Forex/Crypto (5M timeframe minimum)
**Win Rate Claim:** 80% (up to 90-95% with STC confirmation)

---

## ⚠️ DISCLAIMER

> Claims made (80-95% win rate) should be considered marketing hyperbole. Always backtest strategies before live deployment.

---

## Overview

Simple trend-following scalping system using:
1. **Primary:** UT Bot Alert indicator (trend/swing detection)
2. **Confirmation:** STC Oscillator (momentum filter)

---

## Primary Indicator: UT Bot Alert

**Access:** TradingView Indicator Library → Search "UT Bot"

### Setup (Dual Instance Method):

**Instance 1: BUY Signals Only**
- Indicator: UT Bot Alert
- Key Value: `2`
- ATR Period: `1`
- Style: **UNCHECK** Sell option (hide sell signals)

**Instance 2: SELL Signals Only**
- Indicator: UT Bot Alert  
- Key Value: `2`
- ATR Period: `1`
- Style: **UNCHECK** Buy option (hide buy signals)

---

## Confirmation Indicator: STC Oscillator

**Access:** Search "STC oscillator" (momentum oscillator)

### Custom Settings:

| Parameter | Value |
|-----------|-------|
| Length | **80** |
| Fast Length | **27** |

### Visual Settings:
- Plot 1 (main): **Green** (increase opacity)
- Plot 2: **Red** (increase opacity)

---

## Entry Rules

### BUY Trade:
1. ✅ UT Bot shows **buy arrow**
2. ✅ STC line **below green line**
3. ✅ STC line **moving upward**
4. ➡️ Enter long

### SELL Trade:
1. ✅ UT Bot shows **sell arrow**
2. ✅ STC line **above red line**
3. ✅ STC line **moving downward**
4. ➡️ Enter short

---

## Risk Management

| Element | Setting |
|---------|---------|
| **Timeframe** | 5M minimum (no lower) |
| **Stop Loss** | Below/above signal swing low/high |
| **Take Profit** | **2x stop loss** (1:2 R:R) |

### Example Trades:
- Signal quality check: STC must confirm direction
- Trades typically 4:1 R:R mentioned in exam

*[truncated — see source for full prompt]*