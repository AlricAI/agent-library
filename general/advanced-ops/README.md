# Advanced Ops

> Language: [English](advanced-ops.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Advanced Operations (Maintainers)

Language: [English](advanced-ops.md) | [简体中文](advanced-ops.zh-CN.md)

This page contains maintainer-focused commands that are intentionally kept out of the main user onboarding path.

## Advanced Agent Controls

```bash
omnimem codex --project-id <project_id> --drift-threshold 0.62 --cwd /path/to/project
omnimem claude --project-id <project_id> --drift-threshold 0.62 --cwd /path/to/project
omnimem codex --smart --context-budget-tokens 420
omnimem codex --smart --no-delta-context
omnimem codex --context-profile balanced --quota-mode normal --show-context-plan
omnimem codex --context-profile low_quota --quota-mode critical --show-context-plan
omnimem claude --context-profile deep_research --quota-mode low --show-context-plan
omnimem codex --context-profile balanced --quota-mode auto --show-context-plan
omnimem context-plan --prompt "refactor sync daemon retry policy" --context-profile balanced --quota-mode auto
omnimem context-plan --from-runtime --tool codex --project-id OM --context-profile balanced --quota-mode auto
omnimem agent run --tool codex --project-id OM --prompt "..." --retry-max-attempts 4 --retry-initial-backoff 1.5 --retry-max-backoff 12
npm run ci:watch
bash scripts/ci_watch.sh --workflow ci.yml --branch main --max-wait-min 45
```

Context policy flags:

- `--context-profile`: `balanced | low_quota | deep_research | high_throughput`
- `--quota-mode`: `normal | low | critical | auto`
- `--show-context-plan`: print effective budget/retrieve/delta plan before launch
- `omnimem context-plan` now returns `decision_reason` to explain why auto mode selected current quota tier.
- `omnimem context-plan --from-runtime` also returns `recent_context_utilization_used` for utilization-aware auto decisions.
- Auto mode can also tighten quota based on recent transient failures and recent context utilization from local runtime history.

Notes:

- Context prefix is stable by default (timestamp removed) to improve provider prompt-cach

*[truncated — see source for full prompt]*