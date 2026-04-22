---
name: Evaluation Report
description: **Generated**: 2026-02-25 00:41
**Model**: Kimi K2.5 (`bedrock/moonshotai.kimi-k2.5`)
**Benchmark**: Multi-SWE-bench Rust (ByteDance-Seed)
**Framework
model: claude-sonnet-4-5
---
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
> This meant `git diff base_commit HEAD` captured the pre-existing fix artifact
> rather than agent-generated changes. This was corrected via the `base_commit`
> checkout fix applied to `run_infer.py` in this evaluation cycle.


## 5. Cost & Efficiency Metrics

| Metric | Value |
|--------|-------|
| Total LLM API cost | $4.48 |
| Total token usage | 7,289,452 |
| Total LLM calls | 321 |
| Avg cost per instance | $0.345 |
| Avg tokens per instance | 560,727 |


### Multi-Instance Cost Breakdown

| Instance | Cost | Tokens | LLM Calls | Avg Latency |
| --- | --- | --- | --- | --- |
| `BurntSushi__ripgrep-954` | $0.492 | 808,735 | 30 | 7.99s |
| `clap-rs__clap-5527` | $0.489 | 800,509 | 30 | 10.43s |
| `sharkdp__bat-3075` | $0.493 | 799,634 | 30 | 10.18s |
| `sharkdp__fd-1162` | $0.000 | 0 | 0 | 0.00s |
| `tokio-rs__tokio-6462` | $0.692 | 1,095,207 | 30 | 12.28s |
| `BurntSushi__ripgrep-954` | $0.302 | 497,420 | 29 | 2.94s |
| `clap-rs__clap-5527` | $0.291 | 473,999 | 30 | 5.04s |
| `sharkdp__bat-3075` | $0.463 | 758,837 | 30 | 5.55s |
| `sharkdp__fd-1162` | $0.245 | 398,345 | 30 | 4.07s |
| `tokio-rs__tokio-6462` | $0.327 | 533,640 | 30 | 6.44s |



## 6. Agent Behavioral Analysis

*See [trajectory_report.md](trajectory_report.md) for detailed 18-run analysis.*

Key findings from trajectory analysis:

- **65% terminal, 28% views, 4% edits**: Agent heavily favors exploration over modification
- **103 reproduction attempts** across 16 active runs: Dominance of reproduce-then-fix strategy
- **8/18 runs recognized fix exists**: Agent correctly identified pre-existing fix but continued exploring
- **Temperature impact**: T=0.8 yielded 60% edit rate vs 0% at T=0.0
- **No runs called `finish`**: All terminated via `MaxIterationsReached` (30 iterations)


## 7. Failure Mode Taxonomy


| Failure Mode | Count | Description |
|-------------|-------|-------------|
| Reproduction Loop | 6/18 | Agent stuck cycling between test reproduction and exploration |
| Identified Fix Exists | 6/18 | Agent recognized fix but edited anyway (pre-existing fix artifact) |
| SDK Event Mismatch | 2/18 | Message-format events not parsed as ActionEvents |
| Correct Identification | 2/18 | Agent correctly identified fix but didn't call finish |
| Exhaustion with Edits | 1/18 | Agent made edits but ran out of iterations |
| Partial Completion | 1/18 | Agent made progress but hit iteration limit |


## 8. Methodology & Infrastructure


### Evaluation Pipeline
1. **Instance Selection**: 5 instances from distinct repos, all with ≤17-line fix patches
2. **Docker Isolation**: Each instance runs in a pre-built Docker container with the repo at `base_commit`
3. **Agent Execution**: OpenHands CodeAct agent with file_editor + terminal tools
4. **Patch Extraction**: `git diff base_commit HEAD` captures only agent-generated changes
5. **Multi-attempt**: Up to 3 attempts per instance for Pass@K computation

### Key Infrastructure Fixes
- **`base_commit` checkout fix** ([run_infer.py](../benchmarks/multiswebench/run_infer.py)): Added `git checkout {base_commit}` after `git reset --hard` so agents start from the buggy state, not the fixed HEAD
- **`version` field fix** ([build_images.py](../benchmarks/multiswebench/build_images.py)): Deferred `version` lookup to Python-only branch, fixing crash on Rust instances
- **Windows compatibility** ([sitecustomize.py](../sitecustomize.py)): Ensured `_win_compat` module is found via explicit `sys.path` insertion


## 9. Deliverables


| Deliverable | Location | Description |
|------------|----------|-------------|
| Trajectory Analysis | `analysis/trajectory_analysis.py` | 450+ line deep behavioral analyzer |
| Trajectory Report | `analysis/trajectory_report.md` | 9-section behavioral findings |
| Evaluation Report | `analysis/evaluation_report.md` | This comprehensive report |
| Pass@K Calculator | `analysis/pass_at_k.py` | Unbiased Chen et al. metric |
| Multi-instance Dataset | `benchmarks/multiswebench/data/multi_instance_eval.jsonl` | 5-repo curated dataset |
| Pipeline Fixes | `benchmarks/multiswebench/run_infer.py` | base_commit checkout, version field |
| Run Scripts | `scripts/run_multi_instance_eval.ps1` | Reproducible evaluation runner |