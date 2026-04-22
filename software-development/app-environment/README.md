# App Environment

> > **Scope:** Full-stack
> These coding standards and conventions **must be strictly followed** whenever you work on any code that reads, loads, valida

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# App Environment Variables — Agent Instructions

> **Scope:** Full-stack
> These coding standards and conventions **must be strictly followed** whenever you work on any code that reads, loads, validates, or documents environment variables, regardless of the nature of the work (new features, bug fixes, refactoring, or any other changes). If you find any contradiction between the rules in this file and those in any other instruction file (including `AGENTS.md`), **report it immediately and start a discussion** before making any changes.

---

## 1. Overview

All runtime configuration is supplied through environment variables. The backend reads and validates these variables at startup via `backend/config/` (currently `backend/config/env.go`). **Fail-fast behavior is mandatory:** the application must refuse to start if the configuration is invalid or incomplete, printing a clear, human-readable error message to stderr before exiting.

---

## 2. The `LINKSHORTENER_ENV` Mode Selector

`LINKSHORTENER_ENV` controls which configuration sources are consulted at startup. It is a special variable with the following rules:

- It is **always read from the OS environment only.** `.env` files must never override it, regardless of mode or order.
- It must be set explicitly. There is no default.
- **Accepted values are `dev` and `prod` only.** Any other value — including an empty string — must cause the application to exit immediately with a descriptive error message before any other initialization takes place. Example message:

  ```
  FATAL: LINKSHORTENER_ENV must be "dev" or "prod", got "<actual_value>"
  ```

---

## 3. Configuration Loading Algorithm

### 3.1 `dev` mode

Execute the following steps in order:

1. Parse `../.env` (path relative to the Go binary's working directory). If the file does not exist, silently skip it. If it exists but is malformed, abort with a descriptive error.
2. Parse `../.env.dev`. Entries in this file override matching entries from `../.env`. If 

*[truncated — see source for full prompt]*