# Backend Web

> > **Scope:** Backend
> These coding standards and conventions **must be strictly followed** whenever you work on any web-layer code, regardless of the

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Backend Web Layer — Agent Instructions

> **Scope:** Backend
> These coding standards and conventions **must be strictly followed** whenever you work on any web-layer code, regardless of the nature of the work (new features, bug fixes, refactoring, or any other changes). If you find any contradiction between the rules in this file and those in any other instruction file (including `AGENTS.md`), **report it immediately and start a discussion** before making any changes.

---

## 1. Core Principle — Strict Separation of Concerns

**The web layer must contain zero business logic.** Its only responsibilities are:

1. Declare the HTTP contract (Huma registration, viewmodels, validation tags).
2. Validate and deserialize the incoming request via Huma.
3. Map the validated viewmodel to a business logic model using a mapper function.
4. Call the appropriate business logic handler method.
5. Map the handler's result back to a viewmodel (or translate an error into an HTTP error response).
6. Return the HTTP response.

Any logic that goes beyond these six steps belongs in `business-logic/handlers/`. If you are unsure whether something is "business logic", **do not make assumptions — discuss it with the user and act according to their response.**

---

## 2. Directory Layout

All web layer code lives under `backend/web/`:

| Path              | Purpose                                                           |
| ----------------- | ----------------------------------------------------------------- |
| `web/viewmodels/` | Huma input/output structs (request bodies, response schemas)      |
| `web/mappers/`    | Conversion functions between viewmodels and business logic models |
| `web/routes/`     | Huma operation registrations and web handler functions            |

Do not place viewmodels, mappers, or route registrations anywhere outside these directories.

---

## 3. Viewmodels

- Viewmodels are plain Go structs with `json` and `validate` struct tags — and **nothing else**.


*[truncated — see source for full prompt]*