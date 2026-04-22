# Methodology

> This page documents the current benchmarking methodology used by `scfuzzbench`.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Methodology

This page documents the current benchmarking methodology used by `scfuzzbench`.

## Objectives

- Run different fuzzers under equivalent infrastructure and runtime constraints.
- Pin versions and inputs so runs are reproducible.
- Publish enough raw and processed artifacts for independent inspection.
- Use robust, distribution-aware reporting across repeated runs.

## End-to-End Benchmark Flow

### 1) Define and pin benchmark inputs

Core inputs are defined through Terraform vars and/or workflow dispatch:

- Target: `target_repo_url`, `target_commit`
- Mode: `benchmark_type` (`property` or `optimization`)
- Infra: `instance_type`, `instances_per_fuzzer`, `timeout_hours`
- Fuzzer set: `fuzzers` (or default all available)
- Tool versions: `foundry_version`, `echidna_version`, `medusa_version`, `recon_version`

In CI (`.github/workflows/benchmark-run.yml`), inputs are validated before apply (value ranges, formats, and conservative character constraints).

### 2) Compute run identity and benchmark identity

Terraform computes two IDs used across the pipeline:

- `run_id`:
  - Explicit `var.run_id` if provided.
  - Otherwise `time_static.run.unix` (state-stable; repeated applies can reuse it).
- `benchmark_uuid`:
  - `md5(jsonencode(benchmark_manifest))` in `infrastructure/main.tf`.

`benchmark_manifest` includes pinned context such as:

- `scfuzzbench_commit`, `target_repo_url`, `target_commit`
- `benchmark_type`, `instance_type`, `instances_per_fuzzer`, `timeout_hours`
- `aws_region`, `ubuntu_ami_id`
- tool versions and selected `fuzzer_keys`

This means changing any of those manifest fields changes `benchmark_uuid`.

### 3) Provision equivalent runners

Terraform provisions one EC2 instance per `(fuzzer, run_index)` pair:

- Same AMI family for all (`ubuntu_ami_ssm_parameter`).
- Same instance type and timeout budget for all fuzzers in a run.
- AZ auto-selected from offering data for the requested instance type (unless `availability_zone` is explicitly 

*[truncated — see source for full prompt]*