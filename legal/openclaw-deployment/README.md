# Openclaw Deployment

> Blueprint is now wired to treat OpenClaw as the sole agent execution backend.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenClaw Deployment Contract

Blueprint is now wired to treat OpenClaw as the sole agent execution backend. The Blueprint backend remains the business control plane; OpenClaw is the execution sidecar.

## Required environment

Set these on the Blueprint backend:

```bash
OPENCLAW_BASE_URL=https://your-openclaw.internal
OPENCLAW_AUTH_TOKEN=replace_me                     # optional if your service is auth-gated
OPENCLAW_TIMEOUT_MS=20000
OPENCLAW_WAIT_TIMEOUT_MS=60000
OPENCLAW_AGENT_PATH=/agent
OPENCLAW_AGENT_WAIT_PATH=/agent/wait
OPENCLAW_AGENT_CANCEL_PATH_TEMPLATE=/agent/{run_id}/cancel
OPENCLAW_AGENT_ARTIFACTS_PATH_TEMPLATE=/agent/{run_id}/artifacts

OPENCLAW_DEFAULT_MODEL=openai/gpt-5.4
OPENCLAW_WAITLIST_AUTOMATION_MODEL=openai/gpt-5.4
OPENCLAW_INBOUND_QUALIFICATION_MODEL=openai/gpt-5.4
OPENCLAW_POST_SIGNUP_MODEL=openai/gpt-5.4
OPENCLAW_OPERATOR_THREAD_MODEL=openai/gpt-5.4
OPENCLAW_SUPPORT_TRIAGE_MODEL=openai/gpt-5.4
OPENCLAW_PAYOUT_EXCEPTION_MODEL=openai/gpt-5.4
OPENCLAW_PREVIEW_DIAGNOSIS_MODEL=openai/gpt-5.4
OPENCLAW_EXTERNAL_HARNESS_MODEL=openai/gpt-5.4
```

## Required HTTP contract

Blueprint expects these sidecar endpoints:

- `POST /agent`
- `POST /agent/wait`

Blueprint also supports these optional-but-expected endpoints:

- `POST /agent/{run_id}/cancel`
- `GET /agent/{run_id}/artifacts`

The request body sent to `/agent` is shaped like:

```json
{
  "request_id": "uuid",
  "session_key": "string",
  "task_type": "operator_thread",
  "mode": "sync",
  "inputs": {},
  "startup_context": {},
  "policy": {
    "risk_level": "low",
    "requires_approval": false,
    "allowed_domains": [],
    "allowed_tools": [],
    "allowed_skill_ids": [],
    "forbidden_actions": [],
    "artifact_retention_policy": {
      "retain_logs": true,
      "retain_artifacts": true,
      "retention_days": 30
    }
  },
  "artifacts_config": {
    "artifact_targets": [],
    "include_logs": true,
    "include_screenshots": false
  },
  "wait_timeout_ms": 60000,
  "model": "opena

*[truncated — see source for full prompt]*