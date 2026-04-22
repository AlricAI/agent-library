# Alpha Launch Checklist

> Last updated: 2026-03-22

This checklist is the concrete launch gate for `Blueprint-WebApp`.

For autonomous-org launch specifically, also use [autono

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Alpha Launch Checklist

Last updated: 2026-03-22

This checklist is the concrete launch gate for `Blueprint-WebApp`.

For autonomous-org launch specifically, also use [autonomous-org-launch-checklist.md](/Users/nijelhunt_1/workspace/Blueprint-WebApp/docs/autonomous-org-launch-checklist.md). That file is the current source of truth for Hermes/Paperclip readiness.

It is based on the repo's current deployment contract, alpha scripts, and the current implementation state.

## 1. Code Gate

- [ ] `npm run check`
- [ ] `npm run build`
- [ ] `npm run alpha:check`
- [ ] `npm run test:e2e`

Current status on 2026-03-22:

- `check`: passing
- `build`: passing
- `test:e2e`: passing
- `alpha:check`: passing
- `alpha:preflight`: failing because the launch environment is not configured in this workspace

Release rule:

- Do not launch while `alpha:check` is red.

## 2. Environment Gate

The launch environment must satisfy `npm run alpha:preflight`.

Use [`.env.example`](/Users/nijelhunt_1/workspace/Blueprint-WebApp/.env.example) as the source of truth for the required keys and example variable names.
Run `npm run alpha:env` for a grouped view of the currently missing launch env categories.
For Render import specifically, start with [render.required.env.example](/Users/nijelhunt_1/workspace/Blueprint-WebApp/render.required.env.example) and [render.optional.env.example](/Users/nijelhunt_1/workspace/Blueprint-WebApp/render.optional.env.example).

- [ ] Firebase Admin configured
  Required: `FIREBASE_SERVICE_ACCOUNT_JSON` or `GOOGLE_APPLICATION_CREDENTIALS`
- [ ] Field encryption configured
  Required: `FIELD_ENCRYPTION_MASTER_KEY` or `FIELD_ENCRYPTION_KMS_KEY_NAME`
- [ ] Agent runtime configured
  Required: `OPENAI_API_KEY`
  Optional: `OPENAI_DEFAULT_MODEL` and per-lane `OPENAI_*_MODEL` overrides
- [ ] Stripe configured
  Required: `STRIPE_SECRET_KEY`, `STRIPE_CONNECT_ACCOUNT_ID`, `STRIPE_WEBHOOK_SECRET`, `CHECKOUT_ALLOWED_ORIGINS`
- [ ] Alpha automation flags enabled
  Required

*[truncated — see source for full prompt]*