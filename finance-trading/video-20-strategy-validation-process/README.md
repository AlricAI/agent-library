# VIDEO 20 STRATEGY VALIDATION PROCESS

> **Source:** YouTube Algorithmic Trading Education (transcript provided 2026-03-07 08:35 UTC)
**Author:** Advanced quantitative trader (PhD-level metho

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VIDEO 20: Strategy Development & Validation — The 4-Step Process

**Source:** YouTube Algorithmic Trading Education (transcript provided 2026-03-07 08:35 UTC)
**Author:** Advanced quantitative trader (PhD-level methodology)
**Status:** Professional-grade strategy validation framework
**Difficulty:** Advanced
**Prerequisites:** Pine Script basics, statistics understanding

---

## 🎯 THE 4-STEP VALIDATION PROCESS

Every strategy must pass these four tests:

| Step | Test | Purpose | Acceptable P-Value |
|------|------|---------|-------------------|
| **1** | **In-Sample Excellence** | Core strategy performance | Excellent performance, not obviously overfit |
| **2** | **In-Sample Monte Carlo Permutation** | Detect data mining bias | **< 1%** |
| **3** | **Walk-Forward Test** | Out-of-sample performance | Worth trading (subjective) |
| **4** | **Walk-Forward Monte Carlo Permutation** | Validate walk-forward wasn't luck | **< 5%** (single year), **< 1%** (multi-year) |

**Reference:** *"Permutation and Randomization Tests for Trading System Development"* — Timothy Masters (PhD Statistics)

---

## 📊 STEP 0: Strategy Assessment Framework

### The Universal Signal Vector

**Every strategy generates:**
- **Signal vector:** At each bar, position (1 = long, 0 = no position, -1 = short)
- **Returns:** Close-to-close returns shifted forward by 1 bar
- **Strategy returns:** Position signal × shifted returns = attributable P&L per bar

**Why bar-level returns?**
- More data granularity than per-trade returns
- More stable calculations
- Standardized across all strategy types
- **Reference:** "Testing and Tuning Market Trading Systems" by Timothy Masters

---

## 🔬 STEP 1: IN-SAMPLE EXCELLENCE

### Development Stage Questions

**Question 1: Is this excellent?**
- Depends on strategy nature
- Look for periods of inconsistency
- Drill down: why does it work poorly vs. well?
- Can it be improved?
- **Threshold:** Subjective, but should look good

**Question 2: Is this obviously

*[truncated — see source for full prompt]*