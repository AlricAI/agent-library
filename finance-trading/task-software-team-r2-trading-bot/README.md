# TASK SOFTWARE TEAM R2 TRADING BOT

> **Created:** 2026-03-16 16:56 UTC  
**Assigned to:** Software Team (Spindle/CTO, Pipeline, TapTap, BugCatcher)  
**Priority:** HIGH  
**Source:** R2-D

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TASK: R2-D2 Trading Bot - Assigned to Software Team
**Created:** 2026-03-16 16:56 UTC  
**Assigned to:** Software Team (Spindle/CTO, Pipeline, TapTap, BugCatcher)  
**Priority:** HIGH  
**Source:** R2-D2 design specs + Captain's requirements  
**Review by:** R2-D2 upon completion

---

## Overview
Build a standalone multi-exchange cryptocurrency trading bot with R2-D2's 190-point confluence scoring system. This bot will integrate with The Great Cryptonio portfolio manager and support automated trading across multiple exchanges.

---

## Technical Requirements

### Supported Exchanges (5 total)
1. **Kraken** - Primary institutional exchange
2. **Coinbase** - US retail/trading
3. **Gemini** - US regulated exchange
4. **Binance.US Account 1** - Primary Binance account
5. **Binance.US Account 2** - Secondary Binance account (separate credentials)

### Core Technologies
- **Language:** Python 3.10+
- **API Libraries:** 
  - ccxt (unified exchange API)
  - krakenex (Kraken specific)
  - coinbase-advanced-py (Coinbase)
  - python-binance (Binance.US)
- **Data Analysis:** pandas, numpy, TA-Lib
- **Database:** SQLite (local) or PostgreSQL (optional)
- **Config:** YAML for settings

---

## Architecture

```
r2-trading-bot/
├── r2_trading_bot.py          # Main entry point
├── config.yaml                # User configuration
├── exchanges/
│   ├── __init__.py
│   ├── base.py                # Base exchange wrapper
│   ├── kraken_api.py
│   ├── coinbase_api.py
│   ├── gemini_api.py
│   └── binance_us_api.py      # Handles both accounts
├── signal_engine/
│   ├── __init__.py
│   ├── confluence_calculator.py  # R2's 190-point system
│   ├── indicators.py          # Technical indicators
│   └── patterns.py            # Pattern recognition
├── risk_management/
│   ├── __init__.py
│   ├── position_sizing.py
│   ├── stop_loss.py           # ATR-based
│   └── take_profit.py         # ATR-based
├── data/
│   ├── market_data.py         # OHLCV fetching
│   └── storage.py             # 

*[truncated — see source for full prompt]*