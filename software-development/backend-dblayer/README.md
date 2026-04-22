# Backend Dblayer

> > **Scope:** Backend
> These coding standards and conventions **must be strictly followed** whenever you work on any database-layer code, regardless o

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Backend DB Layer — Agent Instructions

> **Scope:** Backend
> These coding standards and conventions **must be strictly followed** whenever you work on any database-layer code, regardless of the nature of the work (new features, bug fixes, refactoring, or any other changes). If you find any contradiction between the rules in this file and those in any other instruction file (including `AGENTS.md`), **report it immediately and start a discussion** before making any changes.

---

## 1. Technology — Non-Negotiable Constraints

| Concern    | Technology                                         |
| ---------- | -------------------------------------------------- |
| ORM        | `github.com/uptrace/bun` with `pgdialect`          |
| DB driver  | `github.com/uptrace/bun/driver/pgdriver`           |
| Database   | PostgreSQL                                         |
| Migrations | `bun/migrate` (Go migration functions, code-first) |

Do not replace or supplement any of these with alternative libraries or tools without explicit user approval.

---

## 2. Directory Layout

All DB layer code lives under `backend/infrastructure/pg/`:

| Path                              | Purpose                                              |
| --------------------------------- | ---------------------------------------------------- |
| `infrastructure/pg/`              | Bun DB setup, connection pool initialization         |
| `infrastructure/pg/models/`       | Bun model structs defining the database schema       |
| `infrastructure/pg/migrations/`   | Numbered, append-only Go migration functions         |
| `infrastructure/pg/mappings/`     | `ToBusinessModel` / `ToDbModel` conversion functions |
| `infrastructure/pg/repositories/` | Concrete repository implementations                  |
| `infrastructure/pg/seed/`         | Static seed data files used in `dev` mode            |

Repository interface definitions belong in `business-logic/interfaces/`. Concrete repository implementations bel

*[truncated — see source for full prompt]*