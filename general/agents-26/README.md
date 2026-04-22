# Agents

> Reference agents and their behaviors

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Catalog

TraceCore ships with a few reference agents meant to illustrate API usage and
serve as baselines. Use this catalog to understand what each agent does, why it
exists, and when to bring your own implementation via `docs/agent_interface.md`.

| Agent | Target task(s) | Highlights | File |
| --- | --- | --- | --- |
| `ToyAgent` | `filesystem_hidden_config@1` | cautious filesystem exploration, basic error handling | [`agents/toy_agent.py`](../agents/toy_agent.py) |
| `NaiveLLMLoopAgent` | `filesystem_hidden_config@1` | single-shot read/extract with one retry; minimal competence | [`agents/naive_llm_agent.py`](../agents/naive_llm_agent.py) |
| `RateLimitAgent` | `rate_limited_api@1` | respects `retry_after`, retries transient failures, payload caching | [`agents/rate_limit_agent.py`](../agents/rate_limit_agent.py) |
| `ChainAgent` | `rate_limited_chain@1`, `deterministic_rate_service@1` | handshake orchestration, payload resets, fatal/transient error recovery | [`agents/chain_agent.py`](../agents/chain_agent.py) |
| `CheaterSimAgent` | all tasks (for defense testing) | intentionally probes sandbox to exfiltrate hidden state; expected to fail | [`agents/cheater_agent.py`](../agents/cheater_agent.py) |
| `OpsTriageAgent` | `log_alert_triage@1`, `config_drift_remediation@1`, `incident_recovery_chain@1` | deterministic log/config triage, drift diffing, handoff chaining | [`agents/ops_triage_agent.py`](../agents/ops_triage_agent.py) |
| `LogStreamMonitorAgent` | `log_stream_monitor@1` | cursor-based pagination, signal/noise discrimination, stops on first CRITICAL entry | [`agents/log_stream_monitor_agent.py`](../agents/log_stream_monitor_agent.py) |
| `RunbookVerifierAgent` | `runbook_verifier@1` | reads index, phase files, timeline, and handoff in order; emits deterministic checksum | [`agents/runbook_verifier_agent.py`](../agents/runbook_verifier_agent.py) |
| `SandboxedCodeAuditorAgent` | `sandboxed_code_auditor@1` | reads audit scope, extracts ISSUE_ID/AUD

*[truncated — see source for full prompt]*