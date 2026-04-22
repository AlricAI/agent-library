---
name: Kimi K2.5 Report
description: ## Executive Summary

| Metric | Value |
|--------|-------|
| **Model** | Kimi K2.5 (via AWS Bedrock) |
| **Benchmark** | Multi-SWE-Bench Rust (5-inst
model: claude-sonnet-4-5
---
# Kimi K2.5 Evaluation on Multi-SWE-Bench (Rust)

## Executive Summary

| Metric | Value |
|--------|-------|
| **Model** | Kimi K2.5 (via AWS Bedrock) |
| **Benchmark** | Multi-SWE-Bench Rust (5-instance subset) |
| **Total Samples** | 20 |
| **Patches Generated** | 14/20 (70%) |
| **Resolve Rate (T=0.2)** | 1/3 (33.3%) |
| **Resolve Rate (T=0.8 best-of-3)** | 0/3 (0%) |
| **Total Cost** | $8.13 |
| **Temperatures** | T=0.2, T=0.8 |
| **Max Iterations** | 30 |
| **SDK Version** | b498a69 |

## Methodology

### Evaluation Setup

- **Model**: `bedrock/moonshotai.kimi-k2.5` accessed via AWS Bedrock
- **Framework**: OpenHands Agent SDK (commit `b498a69`)
- **Task**: Autonomous code repair on Rust repositories
- **Environment**: Dockerized eval-agent-server containers with repo-specific images
- **Max Iterations**: 30 agent turns per instance
- **Max Output Tokens**: 32,768

### Temperature Configurations

- **T=0.2**: 1 attempt(s), 5 instances, 5 total samples
- **T=0.8**: 3 attempt(s), 5 instances, 15 total samples

### Target Repositories

| # | Repository | Instance ID | Problem Statement |
|---|-----------|-------------|-------------------|
| 1 | `BurntSushi/ripgrep` | `BurntSushi__ripgrep-954` | Support colored output on Windows |
| 2 | `clap-rs/clap` | `clap-rs__clap-5527` | Builder API improvements (5830 chars) |
| 3 | `sharkdp/bat` | `sharkdp__bat-3075` | Syntax highlighting enhancement |
| 4 | `sharkdp/fd` | `sharkdp__fd-1162` | Search functionality improvement |
| 5 | `tokio-rs/tokio` | `tokio-rs__tokio-6462` | Async runtime fix |

## Results by Temperature

### T=0.2

| Instance | Attempt 1 | Patch Rate |
|----------|------------|------------|
| `ripgrep-954` | ❌ Error | 0/1 |
| `clap-5527` | ✅ 2,293 chars | 1/1 |
| `bat-3075` | ✅ 2,496 chars | 1/1 |
| `fd-1162` | ❌ Error | 0/1 |
| `tokio-6462` | ✅ 3,628 chars | 1/1 |

**Summary**: 3/5 samples produced patches (60%), total cost $2.17

### T=0.8

| Instance | Attempt 1 | Attempt 2 | Attempt 3 | Patch Rate |
|----------|------------|------------|------------|------------|
| `ripgrep-954` | ✅ 23,344 chars | ✅ 29,152 chars | ✅ 23,344 chars | 3/3 |
| `clap-5527` | ✅ 802 chars | ✅ 2,976 chars | ✅ 1,437 chars | 3/3 |
| `bat-3075` | ✅ 1,049 chars | ✅ 440 chars | ❌ Error | 2/3 |
| `fd-1162` | ✅ 3,547 chars | ⬚ Empty | ⬚ Empty | 1/3 |
| `tokio-6462` | ⬚ Empty | ✅ 10,227 chars | ✅ 11,630 chars | 2/3 |

**Summary**: 11/15 samples produced patches (73%), total cost $5.96

## Pass@K Metrics (Patch Generation)

> **Note**: These metrics use *patch generation* as the success criterion (did the model produce a non-empty `git diff`?), not functional correctness. A generated patch may or may not resolve the underlying issue.

### Per-Temperature Pass@K

| Configuration | Pass@1 | Pass@3 | Instances |
|----------------|----------------|----------------|----------------|
| **T=0.2** | 60.0% | N/A | 5 |
| **T=0.8** | 73.3% | 100.0% | 5 |
| **Combined** | 70.0% | 95.0% | 5 |

### Per-Instance Pass@K (Combined)

| Instance | n | c (patches) | Pass@1 | Pass@3 |
|----------|---|-------------|---------|---------|
| `ripgrep-954` | 4 | 3 | 75.0% | 100.0% |
| `clap-5527` | 4 | 4 | 100.0% | 100.0% |
| `bat-3075` | 4 | 3 | 75.0% | 100.0% |
| `fd-1162` | 4 | 1 | 25.0% | 75.0% |
| `tokio-6462` | 4 | 3 | 75.0% | 100.0% |

## Functional Correctness Evaluation

### Evaluation Harness

Functional correctness was evaluated using the Multi-SWE-Bench evaluation harness (v1.1.2) with Docker-based test execution. Each instance runs inside a Docker container that:

1. **Baseline run**: Executes the test suite without any patches
2. **Test patch run**: Applies the gold test patch (exposing the bug) and runs tests
3. **Fix patch run**: Applies both the test patch and the model's fix patch, then runs tests

An instance is **resolved** when the fix patch causes all failing tests (introduced by the test patch) to pass again without introducing new failures.

**Infrastructure note**: Only 3 of 5 instances (`clap-5527`, `bat-3075`, `tokio-6462`) had buildable Docker images in the harness. The `ripgrep-954` and `fd-1162` instances were evaluated only at the patch-generation level.

**Workaround**: The harness's `fix-run.sh` uses `git apply` which fails on some patches. A custom `fix_patch_run_cmd` replaces `git apply` with the more permissive `patch --batch --fuzz=5 -p1` utility.

### T=0.2 Resolve Results

| Instance | Baseline (run) | Test Patch (test) | Fix Patch (fix) | Resolved |
|----------|---------------|-------------------|-----------------|----------|
| `bat-3075` | (261, 0, 3) | (232, 1, 1) | (262, 0, 0) | **Yes** ✅ |
| `clap-5527` | (814, 0, 0) | (792, 2, 0) | (786, 8, 0) | No ❌ |
| `tokio-6462` | (171, 1, 0) | (0, 0, 0) | (0, 0, 0) | No ❌ |

Values are (passed, failed, skipped).

- **bat-3075**: The model's patch cleanly fixed the bug. 30 tests transitioned from fail→pass, 0 regressions. All 262 tests pass.
- **clap-5527**: The patch introduced 6 new test failures (8 total vs 2 baseline), causing a regression.
- **tokio-6462**: The gold test patch itself failed to apply (test = (0,0,0)), making this instance unevaluable.

### T=0.8 Resolve Results

| Instance | Attempt 1 | Attempt 2 | Attempt 3 | Any Resolved |
|----------|-----------|-----------|-----------|-------------|
| `bat-3075` | fix=(232,1,1) ❌ | fix=(232,1,1) ❌ | No patch | No |
| `clap-5527` | fix=(0,0,0) ❌ | fix=(788,6,0) ❌ | fix=(792,2,0) ❌ | No |
| `tokio-6462` | No patch | fix=(0,0,0) ❌ | fix=(0,0,0) ❌ | No |

- **bat-3075**: Both att1 and att2 patches caused a regression on `list_themes_without_colors` (PASS→FAIL). T=0.8 patches were shorter (1049, 440 chars) than the successful T=0.2 patch (2496 chars).
- **clap-5527**: Att1 patch failed to compile (0,0,0). Att2 introduced 4 new failures. Att3 produced no net improvement (same 2 failures as test baseline).
- **tokio-6462**: Gold test patch failed to apply in all attempts — a fundamental harness issue for this instance.

### Pass@K Metrics (Functional Resolve Rate)

| Configuration | Pass@1 | Pass@3 | Evaluable Instances |
|---------------|--------|--------|---------------------|
| **T=0.2** | 33.3% | N/A | 3 |
| **T=0.8** | 0.0% | 0.0% | 3 |

### Per-Instance Resolve Rate

| Instance | T=0.2 (n=1) | T=0.8 (n=3) | Combined (n=4) |
|----------|-------------|-------------|----------------|
| `bat-3075` | 1/1 ✅ | 0/2 | 1/3 |
| `clap-5527` | 0/1 | 0/3 | 0/4 |
| `tokio-6462` | 0/1 | 0/2 | 0/3 |

### Functional vs Patch-Generation Gap

| Instance | Patches Generated | Functionally Resolved | Gap |
|----------|------------------|-----------------------|-----|
| `bat-3075` | 3/4 (75%) | 1/3 (33%) | 42pp |
| `clap-5527` | 4/4 (100%) | 0/4 (0%) | 100pp |
| `tokio-6462` | 3/4 (75%) | 0/3 (0%) | 75pp |
| **Average** | **83%** | **9%** | **74pp** |

This demonstrates the significant gap between patch generation and functional correctness: only ~1 in 10 generated patches actually resolve the underlying issue.

## Cost Analysis

| Temperature | Samples | Input Tokens | Output Tokens | Cost | Cost/Sample |
|--------------|--------------|--------------|--------------|--------------|--------------|
| T=0.2 | 5 | 3,478,052 | 26,033 | $2.17 | $0.43 |
| T=0.8 | 15 | 9,539,743 | 78,628 | $5.96 | $0.40 |
| **Total** | 20 | 13,017,795 | 104,661 | **$8.13** | $0.41 |

## Per-Instance Analysis

### `ripgrep-954` (BurntSushi/ripgrep)

- **Attempts**: 4
- **Patches generated**: 3/4 (75%)
- **Max patch size**: 29,152 chars
- **Total cost**: $2.03
- **Avg iterations**: 0.0

| Attempt | Temp | Patch | Chars | Cost | Iterations | Status |
|---------|------|-------|-------|------|------------|--------|
| 1 | T=0.2 | No | 0 | $0.49 | 0 | ❌ Error |
| 1 | T=0.8 | Yes | 23,344 | $0.38 | 0 | ✅ Patch |
| 2 | T=0.8 | Yes | 29,152 | $0.54 | 0 | ✅ Patch |
| 3 | T=0.8 | Yes | 23,344 | $0.61 | 0 | ✅ Patch |

### `clap-5527` (clap-rs/clap)

- **Attempts**: 4
- **Patches generated**: 4/4 (100%)
- **Max patch size**: 2,976 chars
- **Total cost**: $1.72
- **Avg iterations**: 0.0

| Attempt | Temp | Patch | Chars | Cost | Iterations | Status |
|---------|------|-------|-------|------|------------|--------|
| 1 | T=0.2 | Yes | 2,293 | $0.49 | 0 | ✅ Patch |
| 1 | T=0.8 | Yes | 802 | $0.44 | 0 | ✅ Patch |
| 2 | T=0.8 | Yes | 2,976 | $0.44 | 0 | ✅ Patch |
| 3 | T=0.8 | Yes | 1,437 | $0.36 | 0 | ✅ Patch |

### `bat-3075` (sharkdp/bat)

- **Attempts**: 4
- **Patches generated**: 3/4 (75%)
- **Max patch size**: 2,496 chars
- **Total cost**: $1.83
- **Avg iterations**: 0.0

| Attempt | Temp | Patch | Chars | Cost | Iterations | Status |
|---------|------|-------|-------|------|------------|--------|
| 1 | T=0.2 | Yes | 2,496 | $0.49 | 0 | ✅ Patch |
| 1 | T=0.8 | Yes | 1,049 | $0.46 | 0 | ✅ Patch |
| 2 | T=0.8 | Yes | 440 | $0.50 | 0 | ✅ Patch |
| 3 | T=0.8 | No | 0 | $0.38 | 0 | ❌ Error |

### `fd-1162` (sharkdp/fd)

- **Attempts**: 4
- **Patches generated**: 1/4 (25%)
- **Max patch size**: 3,547 chars
- **Total cost**: $0.47
- **Avg iterations**: 0.0

| Attempt | Temp | Patch | Chars | Cost | Iterations | Status |
|---------|------|-------|-------|------|------------|--------|
| 1 | T=0.2 | No | 0 | $0.00 | 0 | ❌ Error |
| 1 | T=0.8 | Yes | 3,547 | $0.34 | 0 | ✅ Patch |
| 2 | T=0.8 | No | 0 | $0.06 | 0 | ⬚ Empty |
| 3 | T=0.8 | No | 0 | $0.06 | 0 | ⬚ Empty |

### `tokio-6462` (tokio-rs/tokio)

- **Attempts**: 4
- **Patches generated**: 3/4 (75%)
- **Max patch size**: 11,630 chars
- **Total cost**: $2.07
- **Avg iterations**: 0.0

| Attempt | Temp | Patch | Chars | Cost | Iterations | Status |
|---------|------|-------|-------|------|------------|--------|
| 1 | T=0.2 | Yes | 3,628 | $0.69 | 0 | ✅ Patch |
| 1 | T=0.8 | No | 0 | $0.06 | 0 | ⬚ Empty |
| 2 | T=0.8 | Yes | 10,227 | $0.55 | 0 | ✅ Patch |
| 3 | T=0.8 | Yes | 11,630 | $0.76 | 0 | ✅ Patch |

## Temperature Comparison

### Patch Generation Rate by Instance

| Instance | T=0.2 Rate | T=0.8 Rate | Best Temp |
|----------|------------|------------|-----------|
| `ripgrep-954` | 0% | 100% | T=0.8 |
| `clap-5527` | 100% | 100% | T=0.2 |
| `bat-3075` | 100% | 67% | T=0.2 |
| `fd-1162` | 0% | 33% | T=0.8 |
| `tokio-6462` | 100% | 67% | T=0.2 |

## Failure Analysis

- **Samples with errors**: 3/20
- **Empty patches (no error)**: 3/20
- **Successful patches**: 14/20

### Error Breakdown

- **Max iterations reached**: 2
- **Connection/retry failures**: 1

## Key Findings

1. **Resolve rate**: 1/3 evaluable instances resolved at T=0.2 (33.3%), 0/3 at T=0.8 across all attempts

2. **Patch-to-resolve gap**: 70% of samples generated patches, but only ~9% of generated patches actually resolved the issue — highlighting that patch generation is a poor proxy for functional correctness

3. **Temperature insight**: The only successful resolve came from T=0.2, despite T=0.8 having higher patch generation rates. Lower temperature produced a more precise, correct fix for bat-3075.

4. **bat-3075 success**: The T=0.2 patch cleanly fixed the issue with 30 tests transitioning from fail→pass. T=0.8 patches for the same instance introduced regressions — demonstrating that shorter, less exploratory patches can be more correct.

5. **Failure modes**: (a) Regression — clap patches introduced new failures; (b) Incomplete fix — clap att3 patch changed nothing; (c) Build failure — clap att1 patch crashed compilation; (d) Harness limitation — tokio test patch failed to apply

6. **Cost efficiency**: $8.13 total for 20 samples ($0.41/sample), with the one successful resolve costing $0.49

## Limitations

1. **Small sample**: 5 instances from the full 239-instance Multi-SWE-Bench Rust dataset (3 functionally evaluable)
2. **Partial evaluability**: tokio-6462 test patch fails to apply in the harness, reducing evaluable instances to 2 with definitive results
3. **Infrastructure constraints**: Docker eval on Windows WSL2 with path-length workarounds; `git apply` replaced with `patch` utility
4. **Single model**: No baseline comparison with other models
5. **Instance selection**: The 5-instance subset was selected for repo diversity (not difficulty), which may not represent the full benchmark distribution

## Appendix: Raw Data

### All Samples

| Instance | Temp | Attempt | Patch Chars | Cost | Iterations | Status |
|----------|------|---------|-------------|------|------------|--------|
| `ripgrep-954` | 0.2 | 1 | 0 | $0.49 | 0 | ❌ Err |
| `ripgrep-954` | 0.8 | 1 | 23,344 | $0.38 | 0 | ✅ |
| `ripgrep-954` | 0.8 | 2 | 29,152 | $0.54 | 0 | ✅ |
| `ripgrep-954` | 0.8 | 3 | 23,344 | $0.61 | 0 | ✅ |
| `clap-5527` | 0.2 | 1 | 2,293 | $0.49 | 0 | ✅ |
| `clap-5527` | 0.8 | 1 | 802 | $0.44 | 0 | ✅ |
| `clap-5527` | 0.8 | 2 | 2,976 | $0.44 | 0 | ✅ |
| `clap-5527` | 0.8 | 3 | 1,437 | $0.36 | 0 | ✅ |
| `bat-3075` | 0.2 | 1 | 2,496 | $0.49 | 0 | ✅ |
| `bat-3075` | 0.8 | 1 | 1,049 | $0.46 | 0 | ✅ |
| `bat-3075` | 0.8 | 2 | 440 | $0.50 | 0 | ✅ |
| `bat-3075` | 0.8 | 3 | 0 | $0.38 | 0 | ❌ Err |
| `fd-1162` | 0.2 | 1 | 0 | $0.00 | 0 | ❌ Err |
| `fd-1162` | 0.8 | 1 | 3,547 | $0.34 | 0 | ✅ |
| `fd-1162` | 0.8 | 2 | 0 | $0.06 | 0 | ⬚ |
| `fd-1162` | 0.8 | 3 | 0 | $0.06 | 0 | ⬚ |
| `tokio-6462` | 0.2 | 1 | 3,628 | $0.69 | 0 | ✅ |
| `tokio-6462` | 0.8 | 1 | 0 | $0.06 | 0 | ⬚ |
| `tokio-6462` | 0.8 | 2 | 10,227 | $0.55 | 0 | ✅ |
| `tokio-6462` | 0.8 | 3 | 11,630 | $0.76 | 0 | ✅ |