# Kimi K2.5 Report

> ## Executive Summary

| Metric | Value |
|--------|-------|
| **Model** | Kimi K2.5 (via AWS Bedrock) |
| **Benchmark** | Multi-SWE-Bench Rust (5-inst

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
|

*[truncated — see source for full prompt]*