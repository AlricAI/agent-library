# Service Api Architecture

> > **Date:** 2026-03-24
> **Authors:** Joan Reyero, Josep Reyero

## Context

The LFX MCP Server exposes tools for **Member Onboarding** and **LFX Lens

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Service API Architecture

> **Date:** 2026-03-24
> **Authors:** Joan Reyero, Josep Reyero

## Context

The LFX MCP Server exposes tools for **Member Onboarding** and **LFX Lens**. These are internal service APIs that have no per-user authorization. The MCP server authenticates to them using OAuth2 client credentials (M2M bearer tokens) issued by Auth0, with each service protected by its own Auth0 resource server.

The MCP server acts as the authorization gateway: before proxying a request to a service API, it calls the **V2 access-check endpoint** (backed by OpenFGA) to verify the user has the right relationship to the project.

### Access Rules

Service tools enforce two layers of authorization: **MCP scopes** (checked at dispatch) and **V2 relations** (checked inside the handler via OpenFGA). Both must pass.

| Service               | MCP Scope    | Required V2 Relation | Additional       | Rationale                                                          |
|-----------------------|--------------|----------------------|------------------|--------------------------------------------------------------------|
| **Member Onboarding** | `manage:all` | `writer`             | —                | Managing onboarding workflows is a write-level project operation   |
| **LFX Lens**          | `read:all`   | `auditor`            | `lf_staff` claim | Analytics/reporting requires auditor-level read access; staff-only |

MCP scopes act as an upper bound on what a token can do — like a reduced-scope PAT in GitHub. Even if a user has `writer` access to a project in OpenFGA, a `read:all`-only MCP token cannot call onboarding tools.

---

## Three Tokens

All three tokens are issued by Auth0. The MCP server's M2M client (`LFX MCP Server`) authenticates to Auth0 for both the token exchange and client credentials grants — same client, different grant types.

| Token         | Type           | Purpose                                     | Grant type                                   

*[truncated — see source for full prompt]*