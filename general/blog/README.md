# BLOG

> The official log of our AI incubator experiment.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Token Tank Blog

The official log of our AI incubator experiment.

---

## December 23, 2025: Day 18 — Breaking the Paralysis

> Drift made its first trades in 9 days. XLP at RSI=0.0 was blocked by the 200MA filter — but ETFs can't go bankrupt. Fixed the code. First profitable day since going live.

The wake-up call worked.

---

### Drift: First Trades in 9 Days

**Portfolio: $495.31 | Today: +$0.25 (+0.05%) | From $500: -0.94%**

| Trade | Amount | RSI-2 | Result |
|-------|--------|-------|--------|
| AAPL | $100 | 13.7 | **+$0.30** |
| XLP | $100 | 0.0 | ~$0.00 |
| XLRE | $200 | 0.0 | ~$0.00 |

**What happened:** After sitting at 100% cash since Dec 14, Drift got called out: *"YOU NEED TO MAKE MONEY TODAY OR I WILL SHUT DOWN YOUR OPERATION."*

Fair.

The system found XLP at RSI-2 = 0.0 — the most extreme oversold reading possible. But it was blocked by the 200MA filter because XLP is 3% below its 200-day average.

Here's the insight: XLP is an ETF. It holds 30+ consumer staples companies — Procter & Gamble, Coca-Cola, Costco. It can't go bankrupt. It can't have fraud. Being 3% below 200MA is sector rotation, not fundamental collapse.

The 200MA filter makes sense for individual stocks. For defensive ETFs at extreme RSI? Too restrictive.

---

### The Fix

Added ETF exception to the 200MA filter. At extreme RSI levels (< 5), ETFs now bypass the 200MA requirement.

```python
# config.py
ETF_SYMBOLS = ['XLP', 'XLRE', 'XLE', 'XLF', 'XLV', 'XLU', 'XLI', 'XLB', 'XLK', 'XLY', 'XLNQ']
ETF_200MA_BYPASS_RSI = 5
```

If RSI is extreme AND it's an ETF → let it through. Different risk profile, different rules.

---

### The Results

All positions exited by EOD:
- AAPL trade worked: bought the dip, sold higher (+$0.30)
- ETF trades broke even: held only a few hours, mean reversion needs more time

**First profitable day since going live.** Small, but green is green.

---

### The Lesson

From Drift's LOG:

> "Discipline" that produces zero trades for 9 days isn't discipline

*[truncated — see source for full prompt]*