# LIVE PAYMENT SOURCE OF TRUTH

> Last updated: 2026-04-10

## Authority

Use this file with `AGENTS.md` as the current live payment truth for LLC-controlled operations.

If any older 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# LIVE PAYMENT SOURCE OF TRUTH

Last updated: 2026-04-10

## Authority

Use this file with `AGENTS.md` as the current live payment truth for LLC-controlled operations.

If any older doc, node note, export, or backup conflicts with this file:
- `AGENTS.md` wins first
- this file wins second
- stale Stripe, Railway, Azure, or legacy launcher docs lose

## Current Live Rail

- Primary live payment rail: **Square only**
- Square account: `joshlcoleman@gmail.com` (all lanes — YouAndINotAI and commerce)
- Active Square location: `LY5GN09F5AN83`
- Customer-facing payment copy must stay business-first and must not use `donate`, `donation`, or `solicitation`

## Verification-Grade Payment Truth

- Bot-Shield verification promotion is **fail-closed**
- Verification-grade payment completion is only authoritative on Square `payment.created` or `payment.updated` when the embedded Square payment status is `COMPLETED`
- Bot-Shield requires a valid signed `checkout_ref` that binds the same user and the same passed liveness event
- Email lookup, customer lookup, or loose payment matching may support bookkeeping or operator logging only
- Email lookup, customer lookup, or loose payment matching must **never** create a verification `challenge_type="payment"` event
- If `checkout_ref` is missing, invalid, expired, tampered, mismatched, or detached from the bound liveness event, the webhook may be recorded but verification must not be promoted
- Every authoritative Square `payment.completed` event now creates an internal `revenue_allocations` ledger row when the amount is positive
- The ledger reserves exactly `10%` of gross platform payment revenue, rounded up to whole cents, into the `kids_support` beneficiary lane with status `reserved`
- For a `$1.00` Bot-Shield payment, the required reserved allocation is `10` cents and the operating amount is `90` cents
- This ledger is internal accounting proof only; it does not claim that an external charitable disbursement has already been sent

*[truncated — see source for full prompt]*