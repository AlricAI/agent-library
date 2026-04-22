---
name: TESTING
description: ---

## 1. Testing Philosophy

This project follows **test-driven development for all formula code**. The oracle formulas are the scientific core of t
model: claude-sonnet-4-5
---
# TESTING.md — Testing Requirements and Patterns

---

## 1. Testing Philosophy

This project follows **test-driven development for all formula code**. The oracle formulas are the scientific core of the research — an incorrect formula means incorrect published results. Every formula implementation must have a passing test before it is merged.

The test pyramid:
```
         ▲ Integration tests (DB required, marked @integration, run separately)
        ███ Component tests (mocked external deps, fast)
      ███████ Unit tests (pure functions, no IO, instant)
```

---

## 2. Running Tests

```bash
# All tests (excluding integration)
make test
# → pytest tests/ -v --cov=. --cov-report=term-missing -m "not integration"

# All tests including integration (requires running DB)
INTEGRATION_TESTS=1 make test

# Single file
pytest tests/test_oracle.py -v

# Single test
pytest tests/test_oracle.py::test_r_l1_numerical -v

# Coverage report only
pytest tests/ --cov=. --cov-report=html
open htmlcov/index.html
```

---

## 3. Coverage Requirements

| Module | Required Coverage |
|--------|-----------------|
| `oracle/bounds.py` | **100%** — no exceptions |
| `oracle/breakeven.py` | **100%** — no exceptions |
| `montecarlo/spectrum.py` | ≥ 90% |
| `pipeline/stages/p3_slots.py` | ≥ 90% |
| `ingestion/base.py` | ≥ 90% |
| `ingestion/polymarket.py` | ≥ 80% (mock HTTP) |
| `ingestion/binance.py` | ≥ 80% (mock HTTP) |
| `db/queries.py` | ≥ 80% (integration tests) |
| All other modules | ≥ 70% |

---

## 4. Required Test File: `tests/test_oracle.py`

This file must exist and all tests must pass before any oracle code is considered done. The complete list of required tests:

```python
"""
tests/test_oracle.py

Oracle formula unit tests — 100% coverage required.
All numerical values verified by hand calculation.
"""
from __future__ import annotations
import pytest
import numpy as np
from oracle.bounds import r_l1, r_l2, r_parametric, delta_r_timing, expected_return, ier as compute_ier
from oracle.breakeven import break_even_p


# ─── Fixture ────────────────────────────────────────────────────────────────

@pytest.fixture
def market_a():
    """Standard near-50/50 BTC market. Used for most tests."""
    return {"q0": 0.50, "q_star": 0.35, "f": 0.02, "tau": 0.26}

@pytest.fixture
def market_b():
    """Long-shot market (S1-like). q0 = 0.20."""
    return {"q0": 0.20, "q_star": 0.12, "f": 0.02, "tau": 0.26}

@pytest.fixture
def market_no_fees():
    """Zero-fee play-money market (Manifold baseline)."""
    return {"q0": 0.50, "q_star": 0.35, "f": 0.00, "tau": 0.00}


# ─── Numerical correctness (hard-coded expected values) ─────────────────────

class TestNumericalValues:

    def test_r_l1_standard(self, market_a):
        """R_L1 = (1/q0) * (1-f) * (1-tau) - 1"""
        result = r_l1(**market_a)
        # = (1/0.50) * 0.98 * 0.74 - 1 = 2.0 * 0.7252 - 1 = 0.4504
        assert abs(result - 0.4504) < 1e-4, f"Expected 0.4504, got {result}"

    def test_r_l2_standard(self, market_a):
        """R_L2 = (1/q_star) * (1-f) * (1-tau) - 1"""
        result = r_l2(**market_a)
        # = (1/0.35) * 0.98 * 0.74 - 1 = 2.8571 * 0.7252 - 1 = 1.0721
        assert abs(result - 1.0721) < 1e-4, f"Expected 1.0721, got {result}"

    def test_delta_r_timing_standard(self, market_a):
        """ΔR_timing = (1-f)(1-tau) * (1/q* - 1/q0)"""
        result = delta_r_timing(**market_a)
        # = 0.7252 * (2.8571 - 2.0) = 0.7252 * 0.8571 = 0.6216
        assert abs(result - 0.6216) < 1e-4, f"Expected 0.6216, got {result}"

    def test_r_parametric_alpha_half(self, market_a):
        """R_L(alpha=0.5) = (0.5/q0 + 0.5/q*) * (1-f)(1-tau) - 1"""
        result = r_parametric(alpha=0.5, **market_a)
        # = (1.0 + 1.4286) * 0.7252 - 1 = 2.4286 * 0.7252 - 1 = 0.7612
        assert abs(result - 0.7612) < 1e-4

    def test_breakeven_alpha_1_standard(self, market_a):
        """p*(alpha=1) = q0 / [(1-f)(1-tau)]"""
        result = break_even_p(alpha=1.0, **market_a)
        # = 0.50 / (0.98 * 0.74) = 0.50 / 0.7252 = 0.6895
        assert abs(result - 0.6895) < 1e-4, f"Expected 0.6895, got {result}"

    def test_breakeven_alpha_0_standard(self, market_a):
        """p*(alpha=0) = q* / [(1-f)(1-tau)]"""
        result = break_even_p(alpha=0.0, **market_a)
        # = 0.35 / 0.7252 = 0.4826
        assert abs(result - 0.4826) < 1e-4

    def test_ier_definition(self, market_a):
        """IER = E[R_crowd] / R_L2. E[R_crowd] = (1-f)(1-tau) - 1"""
        r_crowd = (1 - market_a["f"]) * (1 - market_a["tau"]) - 1  # = -0.2748
        r_l2_val = r_l2(**market_a)  # = 1.0721
        ier_val = compute_ier(r_crowd=r_crowd, r_l2=r_l2_val)
        # = -0.2748 / 1.0721 = -0.2563
        assert abs(ier_val - (-0.2563)) < 1e-4

    def test_longshot_market(self, market_b):
        """Long-shot market: high R_L2, low p*"""
        r_l2_val = r_l2(**market_b)
        # = (1/0.12) * 0.98 * 0.74 - 1 = 8.3333 * 0.7252 - 1 = 5.044
        assert abs(r_l2_val - 5.044) < 1e-3
        p_star = break_even_p(alpha=1.0, **market_b)
        # = 0.20 / 0.7252 = 0.2758
        assert abs(p_star - 0.2758) < 1e-4

    def test_no_fee_no_tax(self, market_no_fees):
        """Zero fees: oracle earns gross multiplier - 1"""
        result = r_l1(**market_no_fees)
        # = (1/0.50) * 1.0 * 1.0 - 1 = 2.0 - 1 = 1.0
        assert abs(result - 1.0) < 1e-9


# ─── Structural properties ───────────────────────────────────────────────────

class TestStructuralProperties:

    def test_l2_beats_l1(self, market_a):
        """Layer-2 oracle always beats Layer-1 (q* <= q0 → 1/q* >= 1/q0)"""
        assert r_l2(**market_a) >= r_l1(alpha=1.0, **market_a)

    def test_l2_equals_l1_when_q_star_equals_q0(self):
        """When q* = q0 (no intra-slot movement), L1 = L2"""
        params = {"q0": 0.50, "q_star": 0.50, "f": 0.02, "tau": 0.26}
        assert abs(r_l1(alpha=1.0, **params) - r_l2(**params)) < 1e-9

    def test_parametric_monotone_in_alpha(self, market_a):
        """R_parametric is monotonically non-increasing in alpha"""
        alphas = [0.0, 0.1, 0.25, 0.5, 0.75, 0.9, 1.0]
        returns = [r_parametric(alpha=a, **market_a) for a in alphas]
        for i in range(len(returns) - 1):
            assert returns[i] >= returns[i+1] - 1e-9, \
                f"Non-monotone at alpha={alphas[i]}: {returns[i]} < {returns[i+1]}"

    def test_parametric_at_alpha_0_equals_l2(self, market_a):
        assert abs(r_parametric(alpha=0.0, **market_a) - r_l2(**market_a)) < 1e-9

    def test_parametric_at_alpha_1_equals_l1(self, market_a):
        assert abs(r_parametric(alpha=1.0, **market_a) - r_l1(alpha=1.0, **market_a)) < 1e-9

    def test_random_investor_loses_with_fees(self, market_a):
        """E[R_net](p=0.5) < 0 for any market with positive fees"""
        result = expected_return(p=0.5, alpha=1.0, **market_a)
        assert result < 0, f"Random investor should lose money but got {result}"

    def test_oracle_wins_at_fair_price(self, market_a):
        """E[R_net](p=1.0, alpha=0) > 0 for any market where q* < 1/(1-f)(1-tau)"""
        result = expected_return(p=1.0, alpha=0.0, **market_a)
        assert result > 0, f"Oracle should profit but got {result}"

    def test_expected_return_linear_in_p(self, market_a):
        """E[R_net] is linear in p"""
        r1 = expected_return(p=0.6, alpha=0.5, **market_a)
        r2 = expected_return(p=0.7, alpha=0.5, **market_a)
        r3 = expected_return(p=0.8, alpha=0.5, **market_a)
        # Check equal spacing (linearity)
        assert abs((r2 - r1) - (r3 - r2)) < 1e-9

    def test_multiplicative_drag_worse_than_additive(self, market_a):
        """(1-f)(1-tau) < 1-f-tau for f,tau > 0"""
        f, tau = market_a["f"], market_a["tau"]
        compound = (1 - f) * (1 - tau)
        arithmetic = 1 - f - tau
        assert compound < arithmetic

    def test_breakeven_decreases_with_alpha(self, market_a):
        """p* is non-increasing as alpha decreases (back-loading is better)"""
        p_star_front = break_even_p(alpha=1.0, **market_a)
        p_star_back  = break_even_p(alpha=0.0, **market_a)
        assert p_star_back <= p_star_front

    def test_breakeven_increases_with_fee(self):
        """Higher fees require higher accuracy to break even"""
        params = {"q0": 0.50, "q_star": 0.35, "tau": 0.0}
        p_low_fee  = break_even_p(alpha=1.0, f=0.01, **params)
        p_high_fee = break_even_p(alpha=1.0, f=0.05, **params)
        assert p_high_fee > p_low_fee

    def test_breakeven_increases_with_tax(self):
        """Higher taxes require higher accuracy to break even"""
        params = {"q0": 0.50, "q_star": 0.35, "f": 0.02}
        p_no_tax   = break_even_p(alpha=1.0, tau=0.0, **params)
        p_high_tax = break_even_p(alpha=1.0, tau=0.37, **params)
        assert p_high_tax > p_no_tax


# ─── Error handling ──────────────────────────────────────────────────────────

class TestErrorHandling:

    def test_q_star_zero_raises(self):
        with pytest.raises(ValueError, match="q_star must be positive"):
            r_l2(q0=0.50, q_star=0.0, f=0.02, tau=0.26)

    def test_q_star_negative_raises(self):
        with pytest.raises(ValueError):
            r_l2(q0=0.50, q_star=-0.1, f=0.02, tau=0.26)

    def test_q0_zero_raises(self):
        with pytest.raises(ValueError, match="q0 must be positive"):
            r_l1(q0=0.0, q_star=0.35, f=0.02, tau=0.26)

    def test_alpha_out_of_range_raises(self):
        with pytest.raises(ValueError):
            r_parametric(alpha=1.5, q0=0.50, q_star=0.35, f=0.02, tau=0.26)

    def test_fee_negative_raises(self):
        with pytest.raises(ValueError):
            r_l1(q0=0.50, q_star=0.35, f=-0.01, tau=0.26)

    def test_tau_negative_raises(self):
        with pytest.raises(ValueError):
            r_l1(q0=0.50, q_star=0.35, f=0.02, tau=-0.1)

    def test_ier_with_zero_l2_returns_nan(self):
        """If R_L2 = 0, IER is undefined → return NaN"""
        result = compute_ier(r_crowd=-0.27, r_l2=0.0)
        assert np.isnan(result)
```

---

## 5. Required Test File: `tests/test_slots.py`

```python
"""
tests/test_slots.py

Slot construction logic tests — key edge cases.
"""
import pytest
from datetime import datetime, timezone
from pipeline.stages.p3_slots import compute_slot_id, construct_q_star, validate_slot

class TestSlotId:
    def test_deterministic(self):
        t0 = datetime(2024, 1, 15, 12, 0, 0, tzinfo=timezone.utc)
        id1 = compute_slot_id("polymarket", "0xabc123", t0)
        id2 = compute_slot_id("polymarket", "0xabc123", t0)
        assert id1 == id2

    def test_different_platforms_different_ids(self):
        t0 = datetime(2024, 1, 15, 12, 0, 0, tzinfo=timezone.utc)
        id_poly = compute_slot_id("polymarket", "0xabc123", t0)
        id_kals = compute_slot_id("kalshi", "0xabc123", t0)
        assert id_poly != id_kals

class TestQStar:
    def test_q_star_is_minimum_of_winning_token(self):
        """q* must be minimum of WINNING token only, not all tokens"""
        # YES token prices: [0.45, 0.35, 0.40, 0.48]  ← min = 0.35
        # NO token prices:  [0.55, 0.65, 0.60, 0.52]
        # outcome_yes = True → winning = YES token
        # q* = 0.35 (not 0.35 from NO prices which happen to be higher)
        trades = [
            {"token": "yes", "price": 0.45}, {"token": "no",  "price": 0.55},
            {"token": "yes", "price": 0.35}, {"token": "no",  "price": 0.65},
            {"token": "yes", "price": 0.40}, {"token": "no",  "price": 0.60},
            {"token": "yes", "price": 0.48}, {"token": "no",  "price": 0.52},
        ]
        q_star = construct_q_star(trades, outcome_yes=True)
        assert abs(q_star - 0.35) < 1e-9

    def test_q_star_for_no_win(self):
        """When NO token wins, q* is minimum of NO token prices"""
        trades = [
            {"token": "yes", "price": 0.45}, {"token": "no",  "price": 0.55},
            {"token": "yes", "price": 0.70}, {"token": "no",  "price": 0.30},
        ]
        q_star = construct_q_star(trades, outcome_yes=False)
        assert abs(q_star - 0.30) < 1e-9

    def test_q_star_minimum_floor_applied(self):
        """q* must not be < 0.001"""
        trades = [{"token": "yes", "price": 0.0005}]
        q_star = construct_q_star(trades, outcome_yes=True)
        assert q_star >= 0.001

class TestSlotValidation:
    def test_btc_up_yes_wins_is_clean(self):
        slot = {"btc_return_pct": 0.5, "outcome_yes": True, "data_quality_flag": 0}
        flag = validate_slot(slot)
        assert flag == 0

    def test_btc_up_no_wins_is_disputed(self):
        slot = {"btc_return_pct": 0.5, "outcome_yes": False, "data_quality_flag": 0}
        flag = validate_slot(slot)
        assert flag == 2

    def test_near_zero_btc_move_not_flagged(self):
        """Small moves (|btc_return_pct| < 0.1%) should not trigger dispute flag"""
        slot = {"btc_return_pct": 0.05, "outcome_yes": False, "data_quality_flag": 0}
        flag = validate_slot(slot)
        assert flag == 0  # Too small to determine direction reliably
```

---

## 6. Fixtures and Conftest

```python
# tests/conftest.py

import pytest
import polars as pl
from datetime import datetime, timezone

@pytest.fixture
def sample_slot_master_row() -> dict:
    """A clean, realistic C1 slot for use across tests."""
    return {
        "slot_id":             "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
        "market_id":           "0xabcdef1234567890",
        "class_code":          "C1",
        "platform":            "polymarket",
        "t0_utc":              datetime(2024, 3, 15, 12, 0, 0, tzinfo=timezone.utc),
        "t_close_utc":         datetime(2024, 3, 15, 12, 5, 0, tzinfo=timezone.utc),
        "t_seconds":           300,
        "outcome_yes":         True,
        "q0_yes":              0.52,
        "q0_no":               0.48,
        "q_star_winner":       0.38,
        "sigma_q_winner":      0.04,
        "volume_usd":          12500.0,
        "n_trades":            87,
        "fee_rate":            0.02,
        "gas_usd":             0.0,
        "btc_price_open":      65000.0,
        "btc_price_close":     65350.0,
        "btc_return_pct":      0.538,
        "data_quality_flag":   0,
    }

@pytest.fixture
def sample_trades_df() -> pl.DataFrame:
    """Minimal trades DataFrame for slot construction tests."""
    return pl.DataFrame({
        "market_id": ["0xabc"] * 6,
        "token":     ["yes", "no", "yes", "no", "yes", "no"],
        "price":     [0.52, 0.48, 0.42, 0.58, 0.55, 0.45],
        "size_usd":  [100.0, 80.0, 150.0, 120.0, 200.0, 180.0],
        "ts_ms":     [0, 0, 60000, 60000, 120000, 120000],
    })
```

---

## 7. Integration Tests

Mark with `@pytest.mark.integration`. These require a running TimescaleDB instance.

```python
# tests/test_db_integration.py
import pytest

pytestmark = pytest.mark.integration

def test_slot_upsert_is_idempotent(db_connection, sample_slot_master_row):
    """Inserting the same slot twice produces exactly one row."""
    from db.queries import upsert_slot, count_slots
    slot_id = sample_slot_master_row["slot_id"]

    upsert_slot(db_connection, sample_slot_master_row)
    upsert_slot(db_connection, sample_slot_master_row)  # second upsert

    count = count_slots(db_connection, slot_id=slot_id)
    assert count == 1

def test_oracle_bounds_foreign_key(db_connection, sample_slot_master_row):
    """oracle_bounds must reference a valid slot_id in slot_master."""
    from db.queries import upsert_oracle_bound
    bound = {
        "slot_id": "nonexistent-uuid",
        "alpha": 0.5,
        "tau_label": "it",
        ...
    }
    with pytest.raises(Exception, match="foreign key"):
        upsert_oracle_bound(db_connection, bound)
```

---

## 8. CI Configuration

```yaml
# .github/workflows/test.yml
name: Test

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: "3.12"
      - run: pip install -r requirements.txt
      - run: make lint          # ruff + mypy
      - run: make test          # pytest (no integration tests in CI)
      - run: coverage report --fail-under=80
```