# AGENTS

> Applies to `backend/` (Node.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# backend/AGENTS.md

Applies to `backend/` (Node.js + TypeScript + Express + Prisma).

---

## Output

Return XML per root contract.

`shadcn` is not applicable.

---

## Serena Required When

- Editing handlers/routes
- Editing exported service methods
- Editing models/DTOs/shared types
- Editing auth/permissions
- Editing repository interfaces

Must confirm:
- Symbol definition
- References
- Contract impact

---

## Context7 Required When

- Using unfamiliar stdlib/framework APIs
- Implementing concurrency/async edge cases
- Handling HTTP edge cases
- Writing non-trivial tests
- Unsure of framework behavior

---

## Stack

- Node.js 20.x
- TypeScript strict mode
- Express 4
- Prisma + PostgreSQL
- Zod validation
- Pino logging
- Jest + Supertest
- Firebase Admin auth

## Project Notes (Migrated from Claude)

This section and all rules below capture backend-specific conventions migrated from `backend/claude.md`.

---

## Critical Rules

1. Never use raw SQL when Prisma can express the query.
2. Validate all request input with Zod.
3. Use structured logger utilities; avoid `console.log` in backend flows.
4. Use centralized error classes/middleware.
5. Preserve standardized success/error response envelopes.
6. Apply auth middleware to protected routes.
7. Keep business logic in services, not route handlers.

---

## Contract Discipline

Do NOT, unless explicitly requested:
- Change JSON shape
- Change status codes
- Change auth behavior
- Change DB schema/migrations

If changed:
- Update docs
- Add/update tests
- Provide curl validation examples

---

## Code Quality

Do NOT:
- Ignore cancellation/shutdown concerns
- Swallow errors
- Panic/throw uncontrolled runtime errors in normal flow
- Log secrets or sensitive payloads

Required patterns:
- Service-layer business logic
- Validation before processing
- Consistent response helpers
- Audit logging for mutations affecting user data

---

## Progression and Domain Rules

Progression logic should preserve the existing

*[truncated — see source for full prompt]*