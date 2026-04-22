# Ai Native Gap Closure Board

> This board translates the current autonomy gap list into execution items with explicit ownership, touchpoints, proof, blockers, and done definitions.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI-Native Gap Closure Board

This board translates the current autonomy gap list into execution items with explicit ownership, touchpoints, proof, blockers, and done definitions.

## Must-Fix

| ID | Owner | File/env touchpoints | Proof of completion | Blocker dependencies | Done definition |
|---|---|---|---|---|---|
| MF-01 Launch preflight green | `blueprint-cto` + `ops-lead` | `/Users/nijelhunt_1/workspace/Blueprint-WebApp/scripts/launch-preflight.mjs`, `/Users/nijelhunt_1/workspace/Blueprint-WebApp/DEPLOYMENT.md`, Render/Vercel env config | `npm run alpha:preflight` exits `0` in the real deployment environment and screenshot/log is attached to the launch issue | Firebase Admin credentials, structured automation provider, Stripe secrets, Google service account, Calendar/Sheets IDs, Slack webhook, email transport | Production env is configured so preflight passes without local overrides or skipped checks |
| MF-02 Autonomous workers live | `ops-lead` + `blueprint-chief-of-staff` | `/Users/nijelhunt_1/workspace/Blueprint-WebApp/server/utils/opsAutomationScheduler.ts`, `BLUEPRINT_*_ENABLED` env flags | `/health/ready` shows required automation flags enabled and worker status docs show scheduled runs | MF-01 env completion, Firebase Admin availability | All required autonomous-alpha workers are enabled in production and have at least one successful run recorded |
| MF-03 External systems provisioned | `growth-lead` + `analytics-agent` + `finance-support-agent` | `AUTONOMOUS_ORG.md`, `.env.example`, provider dashboards for PostHog/GA4, SendGrid, OpenRouter video, ElevenLabs | Provider verification screen shows configured state and a live test event/request succeeds for each required provider | Provider accounts, billing, API keys, domain/auth setup | Analytics, email, OpenRouter video, and ElevenLabs are configured with valid credentials in prod |
| MF-04 Readiness green | `blueprint-cto` + `ops-lead` | `/Users/nijelhunt_1/workspace/Blueprint-WebApp/server/routes/h

*[truncated — see source for full prompt]*