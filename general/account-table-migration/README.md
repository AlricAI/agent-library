# Account Table Migration

> > **STATUS: SUPERSEDED**
>
> This migration was **abandoned** on 2026-01-02 in favor of **FastAPI Users** authentication.
> The BetterAuth integration

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Account Table Migration: BetterAuth Integration

> **STATUS: SUPERSEDED**
>
> This migration was **abandoned** on 2026-01-02 in favor of **FastAPI Users** authentication.
> The BetterAuth integration described here was never completed due to persistent timeout issues.
>
> **Current auth system**: FastAPI Users with JWT tokens
> **See**: [authentication.md](./authentication.md) for current documentation

---

**Date**: 2026-01-02
**Final Status**: Superseded by FastAPI Users migration
**Original Branch**: `e2e-user-journey-tests`

## Historical Context

This document preserves the history of an attempted migration from simple password-in-users-table authentication to BetterAuth's OAuth-ready architecture. The migration was abandoned after encountering persistent timeout issues that could not be resolved.

### What Was Attempted

1. **Schema Migration**: Transform users table to separate credentials into accounts table
2. **BetterAuth Integration**: Use BetterAuth v1.4.7 for frontend authentication
3. **Drizzle ORM**: Frontend schema definition for BetterAuth adapter

### Why It Was Abandoned

Despite extensive debugging:

1. **Timeout Issues**: Login requests would hang indefinitely with valid credentials
2. **bcrypt Compatibility**: Initially suspected, but confirmed NOT the issue
3. **Schema Mismatches**: Multiple schema fixes applied but timeouts persisted
4. **Time Constraints**: Decision made to use simpler, proven FastAPI Users library

### Resolution

On 2026-01-02, the decision was made to:

1. **Abandon BetterAuth** - Too many unresolved integration issues
2. **Adopt FastAPI Users** - Production-ready, well-documented Python auth library
3. **Use JWT Tokens** - Stateless authentication with 1-hour lifetime
4. **Delete Frontend Auth Files** - Remove `web-ui/src/lib/auth.ts` and `auth-client.ts`

### Files Deleted After Migration

- `web-ui/src/lib/auth.ts` - BetterAuth client configuration
- `web-ui/src/lib/auth-client.ts` - BetterAuth API client
- `web-ui/

*[truncated — see source for full prompt]*