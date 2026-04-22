# App Auth

> > **Scope:** Full-stack (backend + frontend)
> These coding standards and conventions **must be strictly followed** whenever you work on any authentic

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Authentication — Agent Instructions

> **Scope:** Full-stack (backend + frontend)
> These coding standards and conventions **must be strictly followed** whenever you work on any authentication-related code, regardless of the nature of the work (new features, bug fixes, refactoring, or any other changes). If you find any contradiction between the rules in this file and those in any other instruction file (including `AGENTS.md`), **report it immediately and start a discussion** before making any changes.

---

## 1. Auth Method — Non-Negotiable Constraints

- **Third-party OAuth2/OIDC providers are the only permitted authentication method.** No exceptions.
- **Never implement or accept passwords**, magic links, email/OTP codes, API-key-based user auth, or any other form of credential-based authentication. If a task description implies adding such a mechanism, refuse and flag it to the user.
- No password fields may be added to the database schema, viewmodels, or any API contracts.
- The MVP providers are **Google**, **Microsoft**, and **Facebook**. The architecture must remain open to adding further providers (GitHub, Apple, LinkedIn, etc.) without schema changes.

---

## 2. Backend Auth Architecture

### 2.1 Libraries

| Concern                         | Technology                                          |
| ------------------------------- | --------------------------------------------------- |
| OAuth2/OIDC provider management | `github.com/markbates/goth` + `gothic` sub-package  |
| Transient OAuth state           | `github.com/gorilla/sessions` (signed cookie store) |
| Post-auth session tokens        | `github.com/golang-jwt/jwt/v5`                      |

Do not replace or supplement any of these with alternative libraries without explicit user approval.

### 2.2 OAuth2 Flow

1. Frontend user initiates login → backend `GET /auth/login/{provider}` starts the OAuth2 flow via `gothic.BeginAuthHandler`.
2. Provider redirects back to `GET /auth/callback` with the

*[truncated — see source for full prompt]*