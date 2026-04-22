# App Locking Strategy

> > **Scope:** Full-stack
> These coding standards and conventions **must be strictly followed** whenever you work on any code that involves editing or 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Optimistic Locking Strategy — Agent Instructions

> **Scope:** Full-stack
> These coding standards and conventions **must be strictly followed** whenever you work on any code that involves editing or deleting mutable entities, regardless of the nature of the work (new features, bug fixes, refactoring, or any other changes). If you find any contradiction between the rules in this file and those in any other instruction file (including `AGENTS.md`), **report it immediately and start a discussion** before making any changes.

---

## 1. Overview

This application uses **optimistic concurrency control (OCC)** to prevent lost updates when multiple users (or browser tabs) concurrently edit or delete the same entity. Rather than holding locks while a user fills in a form, the system records _when_ the entity was last modified and rejects any write whose version precondition is stale.

The strategy applies to all mutable entities (currently `ShortenedUrl`). Apply the same pattern to every new mutable entity added in the future.

---

## 2. Business Model — `LastUpdated` Field

- Business models for mutable entities **must not** expose two separate audit fields (`CreatedAt` / `UpdatedAt`).
- Instead, every mutable business model must have exactly one version field:

  ```go
  LastUpdated time.Time
  ```

- `LastUpdated` maps to the `updated_at` column in the corresponding DB model. `CreatedAt` is required in DB models (per [backend-dblayer.md](backend-dblayer.md)) but **must not** be present in business models unless a feature explicitly requires it.
- The mapping function in `infrastructure/pg/mappings/` must assign `dbModel.UpdatedAt → bizModel.LastUpdated`.

---

## 3. Read Flow — Load for Edit or Delete

Whenever a user initiates an edit or a delete, the **latest version** of the entity must be fetched fresh from the database at that moment — never rely on a version already loaded for display purposes.

1. The business handler calls the repository read method (e.g., `G

*[truncated — see source for full prompt]*