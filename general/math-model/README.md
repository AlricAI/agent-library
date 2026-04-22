# MATH MODEL

> This document is the **complete formal specification** of every formula the system must implement.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MATH_MODEL.md — Mathematical Model Specification

This document is the **complete formal specification** of every formula the system must implement. It is the ground truth for `oracle/bounds.py`, `oracle/breakeven.py`, `montecarlo/spectrum.py`, and `tests/test_oracle.py`.

When there is any ambiguity in the code, this document wins.

---

## 1. Notation

| Symbol | Type | Description |
|--------|------|-------------|
| `p` | Float ∈ [0.5, 1.0] | Investor outcome accuracy (probability of predicting the correct binary result) |
| `α` (alpha) | Float ∈ [0, 1] | Front-loading ratio: fraction of budget W placed at slot open t₀ |
| `W` | Float > 0 | Total capital per slot. **Normalised to W = 1 throughout.** |
| `q₀` | Float ∈ (0, 1) | Opening price of the winning token at t₀ (first trade or mid-quote) |
| `q*` | Float ∈ (0, q₀] | Minimum trade price of the (ex-post) winning token during [t₀, t_close) |
| `f` | Float ∈ [0, 1) | Platform fee rate on gross winnings (Polymarket C1: 0.02) |
| `g` | Float ≥ 0 | Gas cost per transaction in USD. **Use g = 0.0 for Phase 0 unless Polygon gas data available.** |
| `τ` (tau) | Float ∈ [0, 1) | Tax rate on net profits. Gross: 0.0, UK: 0.20, Italy: 0.26, US: 0.37 |
| `V` | Float > 0 | Total USD volume traded during the slot |
| `N` | Int > 0 | Number of slots in the analysis horizon |

---

## 2. Gross Return per Slot

### Shares acquired on a correct prediction

The investor splits budget W = 1 across two entry points:

```
S(α, q₀, q*) = α·W/q₀ + (1−α)·W/q*
             = α/q₀ + (1−α)/q*           [since W = 1]
```

Each share of the winning token resolves to $1. Gross payout on correct prediction:

```
Π_gross(correct) = S − 2g = α/q₀ + (1−α)/q* − 2g
```

Gross return on correct prediction:

```
R_gross(correct) = Π_gross − W = α/q₀ + (1−α)/q* − 2g − 1
```

On wrong prediction (full stake lost plus gas):

```
R_gross(wrong) = −W − 2g = −1 − 2g
```

**Phase 0 simplification (g = 0):**

```
R_gross(correct) = α/q₀ + (1−α)/q* − 1
R_

*[truncated — see source for full prompt]*