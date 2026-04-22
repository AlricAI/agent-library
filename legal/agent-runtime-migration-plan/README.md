# Agent Runtime Migration Plan

> Last updated: 2026-03-22

## Goal

Remove OpenClaw from the alpha launch path and run agent-backed automation directly through the OpenAI Responses AP

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Runtime Migration Plan

Last updated: 2026-03-22

## Goal

Remove OpenClaw from the alpha launch path and run agent-backed automation directly through the OpenAI Responses API.

For this repo's current alpha shape, the OpenAI Agents SDK is not required.

## Lane Mapping

### Use direct Responses API

- `waitlist_triage`
  Why: single structured classification task with strict JSON output
- `inbound_qualification`
  Why: single structured recommendation/drafting task with strict JSON output
- `post_signup_scheduling`
  Why: single planning task; real external actions still run in Blueprint code after the model response
- `support_triage`
  Why: single structured routing/drafting task
- `payout_exception_triage`
  Why: single structured finance triage task that must still fail closed to human review
- `preview_diagnosis`
  Why: single structured diagnosis/escalation task
- `operator_thread`
  Why for alpha: still a prompt-in / JSON-out task; multi-agent orchestration is not required to ship the launch path

### Keep separate from the alpha agent runtime

- `external_harness_thread`
  Why: this is already a different execution model and should stay on the ACP harness path rather than being forced into the alpha OpenAI runtime migration

## Why Agents SDK is not needed for alpha

The current tasks are not handoff-heavy, not multi-agent, and not tool-lifecycle-heavy.

They are mostly:

- one request
- one structured result
- local business logic before/after the call

That matches the Responses API directly.

The Agents SDK becomes worth it later if you want:

- richer operator sessions with tool orchestration
- built-in tracing across handoffs
- multiple cooperating agents
- longer-running agent workflows with reusable session state

## Code Changes In This Migration

- Default provider for alpha task definitions moves from `openclaw` to `openai_responses`
- Runtime dispatch chooses adapter by provider instead of forcing `openclaw`
- Alpha launch preflight check

*[truncated — see source for full prompt]*