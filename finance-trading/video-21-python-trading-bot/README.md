# VIDEO 21 PYTHON TRADING BOT

> **Source:** YouTube Algorithmic Trading Tutorial (transcript 2026-03-07 08:35 UTC)
**Status:** Complete production implementation
**Difficulty:** Begi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VIDEO 21: Build a Trading Bot from Scratch in Python

**Source:** YouTube Algorithmic Trading Tutorial (transcript 2026-03-07 08:35 UTC)
**Status:** Complete production implementation
**Difficulty:** Beginner to Intermediate
**Prerequisites:** Python basics, broker API access

---

## 🎯 WHAT YOU'LL BUILD

A **fully automated trading bot** that:
- Connects to broker via API
- Fetches live market data
- Calculates indicators (EMA, ATR)
- Executes EMA crossover strategy
- Places market orders with SL/TP
- Runs continuously in timed loop

---

## 📋 PREREQUISITES

### 1. Python Installation
- Download from **python.org**
- ✅ **Check "Add to PATH" during installation**

### 2. Code Editor
- **VS Code** (recommended)
- Jupyter Notebook (used in video)
- Any Python IDE works

### 3. Broker with API Access
- **OANDA** (used in video)
- Any broker with REST API
- Need: Account ID + API Token

---

## 🔐 STEP 1: Broker API Setup

### Get Credentials (OANDA Example)

**Account ID:**
- Found in account dashboard
- Format: `101-004-1234567-001`

**API Token:**
1. Navigate to: Trading Tools → OANDA API
2. Click "Generate Token"
3. Copy and save securely

### Create Config File

**File:** `config.py`
```python
OANDA_API_KEY = "your_api_token_here"
OANDA_ACCOUNT_ID = "your_account_id_here"
```

**Security:** Never commit this to GitHub. Add to `.gitignore`.

---

## 🔌 STEP 2: API Connection

### Install Required Libraries

```bash
# OANDA Python wrapper
pip install oandapyV20

# Data manipulation
pip install pandas

# Timezone handling
pip install pytz

# Technical indicators
pip install pandas_ta
```

### Import and Connect

```python
# Import config
import config

# Import OANDA API wrapper
from oandapyV20 import API
from oandapyV20.endpoints.instruments import Instruments

# Create API client
api = API(access_token=config.OANDA_API_KEY)

# Test connection
print("API Connection Established")
```

---

## 📊 STEP 3: Fetch Market Data

### Import Endpoints

```python
from oanda

*[truncated — see source for full prompt]*