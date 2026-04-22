# README PINE SCRIPT

> ## Confluence Scoring System with R2-D2 Integration

**Agent:** the-great-cryptonio  
**Strategy:** Confluence-based crypto trading  
**Platform:** Tr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CRYPTONIO Pine Script Strategy
## Confluence Scoring System with R2-D2 Integration

**Agent:** the-great-cryptonio  
**Strategy:** Confluence-based crypto trading  
**Platform:** TradingView  
**Version:** Pine Script v5  
**Created:** 2026-03-07 06:58 UTC  

---

## Overview

This Pine Script implements **Cryptonio's 60-point confluence scoring system** from the technical analysis masterclass (Videos 1-3). It detects candlestick patterns, support/resistance levels, Fair Value Gaps (FVG), Fibonacci alignments, and trend direction to generate high-probability trade signals.

---

## How to Use

### Step 1: Add to TradingView

1. Open TradingView (tradingview.com)
2. Select any crypto chart (BTC/ETH recommended)
3. Open **Pine Editor** (bottom of screen)
4. Copy/paste `CRYPTONIO_CONFLUENCE_STRATEGY.pine`
5. Click **Add to Chart**

### Step 2: Configure Inputs

Click the gear icon ⚙️ next to the strategy name:

| Setting | Default | Description |
|---------|---------|-------------|
| Risk Per Trade | 2% | Position size |
| Confluence Threshold | 60 | Minimum score to trade |
| Min Risk:Reward | 1.5 | Filter low R:R setups |
| Show Patterns | true | Display pattern labels |
| Show FVG | true | Show Fair Value Gaps |
| Show SMA | true | Display EMAs (20/50/200) |

### Step 3: Set Alerts

1. Click **Alerts** (top right clock icon)
2. Click **Create Alert**
3. Select condition: **CRYPTONIO Confluence System**
4. Choose either:
   - 📊 **CRYPTONIO - BUY Signal**
   - 📊 **CRYPTONIO - SELL Signal**
5. **Webhook URL:** Enter your endpoint (e.g., `https://myl0nr0s.cloud:9001/tradingview-webhook`)
6. Click **Create**

---

## Pattern Detection

### 8 Candlestick Patterns (Video 2)

| Pattern | Code | Signal |
|---------|------|--------|
| **Bullish Engulfing** | BE | Reversal at support |
| **Bearish Engulfing** | SE | Reversal at resistance |
| **Hammer** | H | Bullish reversal |
| **Shooting Star** | SS | Bearish reversal |
| **Bullish Marubozu** | MZ | Trend continuation (

*[truncated — see source for full prompt]*