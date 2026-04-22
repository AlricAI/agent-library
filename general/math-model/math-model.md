---
name: MATH MODEL
description: This document is the **complete formal specification** of every formula the system must implement.
model: claude-sonnet-4-5
---
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
R_gross(wrong)   = −1
```

---

## 3. Net Return (After Fee and Tax)

Platform fee `f` is charged on the gross winnings (not on the stake).

Net payout on correct prediction:

```
Π_net(correct) = S · (1 − f) − 2g
               = (α/q₀ + (1−α)/q*) · (1 − f) − 2g
```

Net return on correct prediction, before tax:

```
R_net_pretax(correct) = Π_net − W = (α/q₀ + (1−α)/q*) · (1 − f) − 2g − 1
```

Tax `τ` is applied only to **positive** net profit (losses are not clawed back within a single slot):

```python
if R_net_pretax > 0:
    R_net(correct) = R_net_pretax * (1 − τ)
else:
    R_net(correct) = R_net_pretax  # No tax on losses
```

**Phase 0 simplification (g = 0, and for oracle bounds we compute at-profit returns):**

```
R_net(correct) = (α/q₀ + (1−α)/q*) · (1 − f) · (1 − τ) − 1
R_net(wrong)   = −1
```

> **Implementation note:** For oracle bounds computation, assume the oracle always predicts correctly, so R_net is always R_net(correct). The tax simplification ((1−f)(1−τ) applied directly) is valid because oracle returns are always positive for well-priced markets. For the Monte Carlo, apply the conditional tax rule above.

---

## 4. Expected Net Return: The (p, α) Landscape

The expected net return per slot for an investor with accuracy p and front-loading ratio α:

**Gas-negligible form (Phase 0):**

```
E[R_net](p, α, f, τ) = p · (α/q₀ + (1−α)/q*) · (1−f)(1−τ)  −  1
```

**Structural properties (implement and test all of these):**

1. **Linear in p:** For fixed (α, q₀, q*, f, τ), E[R_net] is linear in p with:
   - Slope: `(α/q₀ + (1−α)/q*) · (1−f)(1−τ)`
   - Intercept: `-1`

2. **Monotone in α:** `∂E[R_net]/∂α = p·(1−f)(1−τ) · (1/q₀ − 1/q*)`
   Since q* ≤ q₀ → 1/q₀ ≤ 1/q* → this derivative is ≤ 0.
   **Back-loading (lower α) always weakly increases expected return.**

3. **Multiplicative drag:** `(1−f)(1−τ) < 1−f−τ` for f,τ > 0.
   The compound factor is always worse than the arithmetic sum.

4. **Class independence of structure:** The formula has the same form for all market classes. Only the distribution of (q₀, q*) varies by class.

---

## 5. Oracle Bounds

### Layer 1 (L1) — Outcome Oracle, Full Front-Load

Perfect outcome prediction, α = 1 (all capital at slot open):

```
R_L1(q₀, f, τ) = (1/q₀) · (1−f) · (1−τ) − 1
```

### Layer 2 (L2) — Dual Oracle: Outcome + Optimal Timing

Perfect outcome prediction, α = 0 (all capital at minimum price q*):

```
R_L2(q*, f, τ) = (1/q*) · (1−f) · (1−τ) − 1
```

### Parametric Oracle — Any α

```
R_L(α, q₀, q*, f, τ) = (α/q₀ + (1−α)/q*) · (1−f) · (1−τ) − 1
```

Verify: R_L(α=1) = R_L1, R_L(α=0) = R_L2. ✓

### Timing Premium

The marginal economic value of knowing the optimal intra-slot entry point:

```
ΔR_timing(q₀, q*, f, τ) = R_L2 − R_L1 = (1−f)(1−τ) · (1/q* − 1/q₀)
```

Note: ΔR_timing is a property of the slot, not of α. It is the same for all α.

### Numerical examples (use in unit tests):

Given: `q₀ = 0.50, q* = 0.35, f = 0.02, τ = 0.26`

```
R_L1 = (1/0.50) × 0.98 × 0.74 − 1 = 2.00 × 0.7252 − 1 = 0.4504
R_L2 = (1/0.35) × 0.98 × 0.74 − 1 = 2.857 × 0.7252 − 1 = 1.0721
ΔR_timing = (1/0.35 − 1/0.50) × 0.7252 = (2.857 − 2.000) × 0.7252 = 0.6217
R_L(α=0.5) = (0.5/0.50 + 0.5/0.35) × 0.7252 − 1 = (1.0 + 1.4286) × 0.7252 − 1 = 0.7612
```

---

## 6. Break-Even Accuracy Surface

Setting E[R_net] = 0 and solving for p:

```
p*(α, f, τ, q₀, q*) = 1 / [(α/q₀ + (1−α)/q*) · (1−f) · (1−τ)]
```

**Limiting cases:**

```
# Full front-load (α = 1):
p*(1, f, τ) = q₀ / [(1−f)(1−τ)]

# Pure timing oracle entry (α = 0):
p*(0, f, τ) = q* / [(1−f)(1−τ)]
```

**Cross-class examples (for paper and dashboard):**

| Market | q₀ | q* | f | τ (IT) | p*(α=1) | p*(α=0) |
|--------|----|----|---|--------|---------|---------|
| BTC 5-min (C1) | 0.50 | 0.35 | 0.02 | 0.26 | 0.692 | 0.484 |
| Fed cut (P2) | 0.40 | 0.25 | 0.02 | 0.26 | 0.554 | 0.346 |
| Election (P1) | 0.55 | 0.35 | 0.02 | 0.26 | 0.761 | 0.484 |

**Implementation:** Use `scipy.optimize.brentq` over the interval (0.5, 1.0):

```python
from scipy.optimize import brentq

def break_even_p(alpha, f, tau, q0, q_star) -> float:
    def objective(p):
        return expected_return(p, alpha, q0, q_star, f, tau)
    if objective(1.0) <= 0:
        return 1.0  # Oracle cannot break even (market too efficient / fee too high)
    if objective(0.5) >= 0:
        return 0.5  # Random agent already profitable (should not occur with positive fees)
    return brentq(objective, 0.5, 1.0, xtol=1e-6)
```

---

## 7. Information Efficiency Ratio (IER)

### Crowd Reference Return

The "crowd" is modelled as an agent who:
- Treats the opening price q₀ as the fair probability of YES winning
- Bets a fixed stake W = 1 at q₀ (full front-load, α = 1)
- Is correct with probability q₀ (i.e., the market is calibrated)

Expected gross crowd return:

```
E[R_crowd_gross] = q₀ · (1/q₀ − 1) + (1 − q₀) · (−1)
                 = (1 − q₀) − (1 − q₀)
                 = 0
```

Wait — this gives zero gross return for a calibrated market. That's correct: a calibrated market with no fees has E[R] = 0 for a bettor who bets at fair odds. With fees:

```
E[R_crowd_net](f, τ) = q₀ · [(1/q₀)(1−f)(1−τ) − 1] + (1 − q₀) · (−1)
                     = (1−f)(1−τ) − q₀ − (1 − q₀)
                     = (1−f)(1−τ) − 1
```

This simplifies to a constant independent of q₀: `E[R_crowd_net] = (1−f)(1−τ) − 1`.

For Polymarket with f=0.02, τ=0.26: `E[R_crowd_net] = 0.98 × 0.74 − 1 = −0.2748`. The crowd always loses money in expectation in a calibrated market with fees — a key result.

### IER Definition

```
IER(t) = E[R_crowd_net] / R_L2(t)
```

Where R_L2(t) is the Layer-2 oracle return for slot t.

**Range:** IER ∈ [0, 1] when the market is well-priced. IER > 1 theoretically impossible (crowd cannot beat oracle). IER < 0 means oracle itself loses money (over-efficient pricing + fees — can occur in very efficient markets).

**Implementation note:** If R_L2(t) ≤ 0 (oracle loses money), set IER = NaN and exclude from IER analysis. Flag the slot as `data_quality_flag = max(flag, 1)`.

---

## 8. Multi-Slot Accumulation

For N independent slots with reinvestment and constant (p, α, f, τ):

```
V_N(p, α) = W · ∏ₙ₌₁ᴺ [1 + R_net_n]
```

Where `R_net_n` is the realised net return for slot n (either R_net_correct or R_net_wrong, depending on whether the investor predicted correctly).

For i.i.d. slots (identical q₀, q*):

```
E[V_N] ≈ W · (1 + E[R_net])^N      [geometric growth]
```

**In the Monte Carlo:** Do NOT use the i.i.d. approximation. Use the actual per-slot q₀ and q* values from the empirical slot sequence (the market primitives vary slot-to-slot).

---

## 9. Liquidity-Adjusted Oracle Ceiling (Phase 1 Extension)

For capital W > 1 (the W = 1 normalisation is relaxed), Kyle (1985) price impact:

```
q_impact(W) = q₀ + λ · W · sign(position)
```

Where `λ` is the Kyle price-impact coefficient (estimated from order book depth data: `λ = q_range / (2 × depth_bid_2pct_usd)`).

Liquidity-adjusted Layer-2 oracle return:

```
R_L2_liq(W) = [1 / (q* + λW)] · (1−f)(1−τ) − 1
```

Maximum oracle capital W* (set R_L2_liq = 0 and solve):

```
W*(q*, f, τ, λ) = [1/((1−f)(1−τ))] / λ − q*/λ
                = [1 − q*(1−f)(1−τ)] / [λ(1−f)(1−τ)]
```

**This is a Phase 1 feature.** Implement with a `NotImplementedError` stub in Phase 0:

```python
def oracle_scalability_ceiling(q_star, f, tau, lambda_kyle) -> float:
    raise NotImplementedError("Phase 1: requires order book depth data")
```

---

## 10. Kelly-Optimal Alpha (Phase 1 Extension)

The front-loading ratio α that maximises log-utility (Kelly growth rate):

```
α_K*(p, q₀, q*, f, τ) = argmax_α E[log(1 + R_net(α))]
                       = argmax_α {p · log(1 + R_net_correct(α)) + (1−p) · log(1 + R_net_wrong)}
```

Since R_net_wrong = −1, `log(1 + (−1)) = log(0) = −∞`, the Kelly criterion implies **never bet your entire bankroll** (fractional Kelly).

For a fractional Kelly bet (bet fraction `b` of bankroll, not the full W = 1):

```
b_K* = argmax_b E[log(1 + b · R_net(α))]
```

**This is a Phase 1 extension.** Stub only in Phase 0.

---

## 11. Implementation Checklist for `oracle/bounds.py`

All of the following are implemented as scalar functions in `src/oracle_gap/oracle/bounds.py`:

- [x] `gross_multiplier(alpha, q0, q_star)` → `α/q₀ + (1−α)/q*`
- [x] `r_l1(q0, q_star, f, tau)` → Layer-1 oracle return
- [x] `r_l2(q0, q_star, f, tau)` → Layer-2 oracle return
- [x] `r_parametric(alpha, q0, q_star, f, tau)` → Parametric oracle at α
- [x] `delta_r_timing(q0, q_star, f, tau)` → Timing premium
- [x] `e_r_crowd(f, tau)` → Crowd expected return (simplifies to `(1−f)(1−τ) − 1`)
- [x] `ier(r_crowd, r_l2)` → IER = E[R_crowd] / R_L2
- [x] `break_even_p(alpha, q0, q_star, f, tau)` → Break-even accuracy (in `breakeven.py`)
- [x] `expected_return(p, alpha, q0, q_star, f, tau)` → Full E[R_net] formula

All functions:
1. ✅ Accept scalar inputs (for unit tests) — 35 tests pass
2. ⬜ Work as Polars expressions (Phase 0b — vectorised compute_oracle_bounds)
3. ✅ Raise `ValueError` if `q_star <= 0` or `q0 <= 0`
4. ✅ Return `float` (scalar)

---

## 12. Implementation Checklist for `montecarlo/spectrum.py`

The Numba function signature:

```python
@numba.njit(parallel=True, cache=True)
def simulate_spectrum(
    r_correct: np.ndarray,   # shape (N_slots, N_alpha) — net returns when correct
    r_wrong: np.ndarray,     # shape (N_slots,) — net returns when wrong (= -1.0 - gas)
    p_grid: np.ndarray,      # shape (N_p,) — accuracy values
    n_runs: int,             # number of Monte Carlo runs
    seed: int,               # random seed for reproducibility
) -> np.ndarray:             # shape (N_p, N_alpha, N_runs, N_slots) — cumulative wealth paths
```

Post-processing (in Python, outside Numba):

```python
# Summary statistics over the wealth paths tensor
mean_final_wealth    = wealth_paths[:, :, :, -1].mean(axis=2)   # (N_p, N_alpha)
pct_5_final_wealth   = np.percentile(wealth_paths[:, :, :, -1], 5, axis=2)
pct_95_final_wealth  = np.percentile(wealth_paths[:, :, :, -1], 95, axis=2)
ruin_probability     = (wealth_paths[:, :, :, -1] < 0.5).mean(axis=2)  # < 50% of initial
```

The grid definitions (as module constants in `montecarlo/spectrum.py`):

```python
P_GRID     = np.array([0.50, 0.55, 0.60, 0.65, 0.70, 0.75, 0.80, 0.85, 0.90, 0.95, 1.00])
ALPHA_GRID = np.array([0.00, 0.10, 0.25, 0.50, 0.75, 0.90, 1.00])
N_RUNS     = 10_000
```