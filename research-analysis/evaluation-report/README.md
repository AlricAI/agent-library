# Evaluation Report

> **Generated**: 2026-02-25 00:41
**Model**: Kimi K2.5 (`bedrock/moonshotai.kimi-k2.5`)
**Benchmark**: Multi-SWE-bench Rust (ByteDance-Seed)
**Framework

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Multi-SWE-bench Rust Evaluation Report

**Generated**: 2026-02-25 00:41
**Model**: Kimi K2.5 (`bedrock/moonshotai.kimi-k2.5`)
**Benchmark**: Multi-SWE-bench Rust (ByteDance-Seed)
**Framework**: OpenHands Agent SDK


## 1. Evaluation Design

This evaluation assesses Kimi K2.5's capability on real-world Rust bug-fixing tasks
from 5 distinct open-source repositories, measuring:

- **Patch generation quality**: Whether the agent produces syntactically valid diffs
- **Cross-repo generalization**: Performance variation across different codebases
- **Behavioral patterns**: Tool usage, exploration strategy, iteration budget usage
- **Cost efficiency**: Token usage and API cost per instance


## 2. Cross-Repository Results

| Repository | Issue # | Runs | Has Patch | Avg Actions | Avg Cost |
| --- | --- | --- | --- | --- | --- |
| `BurntSushi/ripgrep` | 954 | 2 | 0/2 | 30 | $0.397 |
| `clap-rs/clap` | 5527 | 2 | 1/2 | 30 | $0.390 |
| `sharkdp/bat` | 3075 | 2 | 1/2 | 30 | $0.478 |
| `sharkdp/fd` | 1162 | 2 | 0/2 | 15 | $0.123 |
| `tokio-rs/tokio` | 6462 | 2 | 1/2 | 30 | $0.510 |

**Overall Patch Rate**: 3/10 (30%)


## 3. Patch Quality Analysis

| Instance | Files Changed | Lines +/- | Key Files |
| --- | --- | --- | --- |
| `clap-rs__clap-5527` | 4 | +35/-6 | Cargo.toml, clap_builder/src/parser/parser.rs, examples/test_num_args.rs (+1) |
| `sharkdp__bat-3075` | 3 | +41/-0 | src/bin/bat/main.rs, test_theme_completion.sh, test_theme_output.sh |
| `tokio-rs__tokio-6462` | 3 | +67/-0 | test_if_let.rs, tokio/src/macros/select.rs, tokio/tests/test_if_let.rs |



## 4. Single-Instance Deep Analysis (ripgrep #1642)

**Total runs**: 3 across 4 temperature settings

- Patch generation rate: 3/3 (100%)
- Total inference cost: $0.69
- Average actions per run: 10.0

> **Important**: The original 18 single-instance runs started from a Docker image
> where the fix was already applied (IMAGE_HEAD=5fbc4fe, base_commit=7099e17).
> This meant `git diff base_commit HEAD` captured the pre-exis

*[truncated — see source for full prompt]*