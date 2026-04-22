# Operations

> This page contains the practical setup and execution details for running `scfuzzbench`.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Operations Guide

This page contains the practical setup and execution details for running `scfuzzbench`.

## Benchmark Inputs

Set inputs via `-var`/`tfvars` (`TF_VAR_*` also works):

- `target_repo_url`, `target_commit`
- `benchmark_type` (`property` or `optimization`)
- `instance_type`, `instances_per_fuzzer`, `timeout_hours`
- `fuzzers` (allowlist; empty means all available)
- fuzzer versions (`foundry_version`, `echidna_version`, `medusa_version`, `recon_version`)
- `git_token_ssm_parameter_name` (for private repos)
- `fuzzer_env` values such as `SCFUZZBENCH_PROPERTIES_PATH`

Per-fuzzer environment variables are documented in `fuzzers/README.md`.

## Quick Start

```bash
make terraform-init
make terraform-deploy TF_ARGS="-var 'ssh_cidr=YOUR_IP/32' -var 'target_repo_url=REPO_URL' -var 'target_commit=COMMIT'"
```

## Local `.env` (Recommended)

```bash
# Usage: source .env
export AWS_PROFILE="your-profile"
export EXISTING_BUCKET="scfuzzbench-logs-..."
export TF_VAR_target_repo_url="https://github.com/org/repo"
export TF_VAR_target_commit="..."
export TF_VAR_timeout_hours=1
export TF_VAR_instances_per_fuzzer=4
export TF_VAR_fuzzers='["echidna","medusa","foundry","recon-fuzzer"]'
export TF_VAR_git_token_ssm_parameter_name="/scfuzzbench/recon/github_token"
export TF_VAR_foundry_git_repo="https://github.com/aviggiano/foundry"
export TF_VAR_foundry_git_ref="fail_on_assert"
```

For Foundry runs, use [aviggiano/foundry](https://github.com/aviggiano/foundry/tree/fail_on_assert).
Current analysis expects the branch's `event: failure` JSON events.

## Re-run A Benchmark

Runners are one-shot. To execute again with a fresh run prefix:

```bash
export TF_VAR_run_id="$(date +%s)"
make terraform-destroy-infra TF_ARGS="-auto-approve -input=false"
make terraform-deploy TF_ARGS="-auto-approve -input=false"
```

## Remote State Backend

1. Create backend resources:

```bash
aws s3api create-bucket --bucket <state-bucket> --region us-east-1
aws s3api put-bucket-versioning --buck

*[truncated — see source for full prompt]*