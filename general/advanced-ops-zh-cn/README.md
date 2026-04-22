# Advanced Ops.Zh CN

> English: [advanced-ops.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 高级运维与评测（维护者）

English: [advanced-ops.md](advanced-ops.md)

本页汇总维护者/研发向命令，避免主 README 对普通用户造成干扰。

## Agent 高级控制

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

上下文策略参数：

- `--context-profile`: `balanced | low_quota | deep_research | high_throughput`
- `--quota-mode`: `normal | low | critical | auto`
- `--show-context-plan`: 启动前打印实际生效的上下文预算/检索/增量策略
- `omnimem context-plan` 现会返回 `decision_reason`，解释 auto 模式为何进入当前配额档位。
- `omnimem context-plan --from-runtime` 还会返回 `recent_context_utilization_used`，用于利用率感知的 auto 决策。
- auto 模式还会结合本地近期瞬时失败历史与上下文利用率自动收紧配额档位。

说明：

- 默认使用稳定上下文前缀（移除时间戳）以提升 provider 侧 prompt cache 命中率。
- `critical` 配额模式会更激进地收缩上下文和检索宽度，降低 token 压力。
- 在 agent/oneshot 路径下，针对瞬时失败（429/overloaded/timeout/5xx）已启用指数退避重试。
- 若错误文本包含 `retry-after` 提示，OmniMem 会将其作为退避等待下限。
- `omnimem agent run` 输出已包含 `tool_attempts`、`tool_retried`、`tool_transient_failures`，便于观察重试行为。
- `omnimem agent run` 还会输出上下文效率字段：`context_budget_tokens`、`context_estimated_tokens`、`context_utilization` 及 core/expand 

*[truncated — see source for full prompt]*