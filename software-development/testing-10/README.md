# Testing

> This guide outlines how to test NeMo RL using unit and functional tests, detailing steps for local or Docker-based execution, dependency setup, and me

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Test NeMo RL

This guide outlines how to test NeMo RL using unit and functional tests, detailing steps for local or Docker-based execution, dependency setup, and metric tracking to ensure effective and reliable testing.

## Unit Tests

> [!IMPORTANT]
> Unit tests require 2 GPUs to test the full suite.

> [!TIP]
> Some unit tests require setting up test assets which you can download with: 
> ```sh
> uv run tests/unit/prepare_unit_test_assets.py
> ```


```sh
# Run the unit tests using local GPUs

# Configuration 1: Default tests only - excludes both hf_gated and mcore tests
uv run --group test bash tests/run_unit.sh

# Configuration 2: Default + HF gated tests, excluding mcore tests
uv run --group test bash tests/run_unit.sh --hf-gated

# Configuration 3: ONLY mcore tests, excluding ones with hf_gated
uv run --extra mcore --group test bash tests/run_unit.sh --mcore-only

# Configuration 4: ONLY mcore tests, including ones with hf_gated
uv run --extra mcore --group test bash tests/run_unit.sh --mcore-only --hf-gated
```

### Experimental: Faster Local Test Iteration with pytest-testmon

We support `pytest-testmon` to speed up local unit test runs by re-running only impacted tests. This works for both regular in-process code and out-of-process `@ray.remote` workers via a lightweight, test-only selection helper.

Usage:
```sh
# Re-run only impacted unit tests
uv run --group test pytest --testmon tests/unit

# You can also combine with markers/paths
uv run --group test pytest --hf-gated --testmon tests/unit/models/policy/test_dtensor_worker.py
```

What to expect:
- On the first run in a fresh workspace, testmon may run a broader set (or deselect everything if nothing was executed yet) to build its dependency cache.
- On subsequent runs, editing non-remote code narrows selection to only the tests that import/use those modules.
- Editing code inside `@ray.remote` actors also retriggers impacted tests. We maintain a static mapping from test modules to transitive `nemo_rl

*[truncated — see source for full prompt]*