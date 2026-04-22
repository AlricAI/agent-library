# TESTING

> ---

## 1. Testing Philosophy

This project follows **test-driven development for all formula code**. The oracle formulas are the scientific core of t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
fro

*[truncated — see source for full prompt]*