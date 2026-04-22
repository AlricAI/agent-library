# Worker Pipeline Patterns

> ## Status Flow

`queued → resolving → generating → autofilling → draft → submitting → submitted`

Phase 3 form filling (draft mode) uses `autofilling`

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Worker & Pipeline Patterns

## Status Flow

`queued → resolving → generating → autofilling → draft → submitting → submitted`

Phase 3 form filling (draft mode) uses `autofilling`; `submitting` is only used for explicit approved submissions.

## Auto-Retry

Transient failures (rate limits, timeouts, auto-fix busy) are auto-retried up to `MAX_AUTO_RETRIES` (default 3). Workday `service_unavailable` outcomes also use this transient retry path. Provider-wide OpenAI/Gemini capacity failures requeue separately as `llm_rate_limited` without consuming the normal fix-attempt budget. After exhaustion of the normal transient budget, jobs go to `stopped` with a suggestion.

## Rate Limiting

- Per-provider concurrency semaphores (`LLM_PROVIDER_CONCURRENCY`, default 15) + in-place rate-limit retry (up to `RATE_LIMIT_RETRIES`, default 5, with exponential backoff 5s→120s) before falling back to the next automation provider in the OpenAI/Gemini chain + staggered worker job starts.
- When both automation providers are exhausted by rate limits, the worker requeues the affected job with `retry_after`, records `llm_rate_limit_retry`, and applies a short global LLM cooldown so queued jobs do not immediately burn the same exhausted providers.
- JD fetch retry: up to `JD_FETCH_MAX_RETRIES` (default 3) with exponential backoff (20s→40s→80s) + 2s delay between individual extraction attempts.

## Auto-Fix Concurrency

`AUTO_FIX_CONCURRENCY` (default 3, was 1). Each auto-fix invokes the configured provider through the shared fix-mode command path.

## Draft Completeness

Drafts require resume PDF + cover letter PDF + current-attempt autofill report + current-attempt screenshot, and every extracted field must be explicitly accounted for, including optionals. Repairable audit failures requeue up to three times using a separate audit-attempt counter. After the third failed repair cycle, the job lands in `stopped` with `failure_type = audit_failure`.

Exhausted audit failures also write human-r

*[truncated — see source for full prompt]*