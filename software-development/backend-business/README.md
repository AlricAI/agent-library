# Backend Business

> > **Scope:** Backend
> These coding standards and conventions **must be strictly followed** whenever you work on any business logic code, regardless o

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Backend Business Logic — Agent Instructions

> **Scope:** Backend
> These coding standards and conventions **must be strictly followed** whenever you work on any business logic code, regardless of the nature of the work (new features, bug fixes, refactoring, or any other changes). If you find any contradiction between the rules in this file and those in any other instruction file (including `AGENTS.md`), **report it immediately and start a discussion** before making any changes.

---

## 1. Directory Layout

Business logic code lives under `backend/business-logic/`:

| Path                         | Purpose                                                                        |
| ---------------------------- | ------------------------------------------------------------------------------ |
| `business-logic/models/`     | Pure Go domain model structs (no ORM or HTTP tags)                             |
| `business-logic/interfaces/` | Pure Go interfaces: repository contracts, service contracts                    |
| `business-logic/handlers/`   | Pure Go business logic handlers; no HTTP or third-party framework dependencies |

Auth-specific handler conventions are governed by [app-auth.md](app-auth.md). DB layer conventions are governed by [backend-dblayer.md](backend-dblayer.md). Web layer conventions (viewmodels, mappers) are governed by [backend-web.md](backend-web.md).

---

## 2. Business Logic Models

- Models in `business-logic/models/` are **plain Go structs** — no `bun`, `json`, or `validate` struct tags.
- They represent domain concepts only. A model struct must not know about database storage, HTTP serialization, or any external framework.
- They are the single shared vocabulary between handlers and repository/service interfaces. All interface method signatures must use these types.
- When a domain concept requires different shapes at the DB or HTTP layer, create a separate DB model or viewmodel and add a mapping function. Do not add tags or fields to t

*[truncated — see source for full prompt]*