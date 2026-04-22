# API IMPROVEMENTS FUTURE

> **Date Created**: 2025-12-03
**Last Updated**: 2026-01-06
**Context**: PR #37 - Multi-Agent Per Project Architecture
**Status**: Backlog - Production 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API Improvements for Future Development

**Date Created**: 2025-12-03
**Last Updated**: 2026-01-06
**Context**: PR #37 - Multi-Agent Per Project Architecture
**Status**: Backlog - Production hardening improvements

> **Note**: MVP is complete as of Sprint 10 (2025-11-23). These improvements are now prioritized
> for production hardening rather than "post-MVP" work. Review priority based on production needs.

---

## Overview

During the code review of PR #37, several API structure improvements were identified that would enhance consistency, scalability, and developer experience. These improvements are documented here for a future development session when we focus on API maturity and production readiness.

---

## 1. API Versioning

### Current State
- All endpoints are unversioned (e.g., `/api/projects/{id}/agents`)
- Breaking changes would require careful coordination with frontend

### Proposed Improvement
Add version prefix to all API routes to enable graceful evolution:

```python
# Before
@app.get("/api/projects/{project_id}/agents")

# After
@app.get("/api/v1/projects/{project_id}/agents")
```

**Benefits**:
- Allows introducing breaking changes in v2 while maintaining v1
- Standard industry practice for production APIs
- Easier to deprecate old endpoints

**Implementation Strategy**:
1. Add version prefix to all routes (`/api/v1/...`)
2. Update frontend API client to use versioned endpoints
3. Document versioning policy in API docs
4. Consider version negotiation header: `Accept: application/vnd.codeframe.v1+json`

---

## 2. Consistent Response Envelopes

### Current State
Mixed response formats across endpoints:
- Some return bare objects: `GET /api/projects/{id}` → `{...project}`
- Some return bare arrays: `GET /api/projects/{id}/agents` → `[...agents]`
- Some return wrapped: `POST /api/projects/{id}/agents` → `{"assignment_id": 42, "message": "..."}`

### Proposed Improvement
Standardize on consistent envelope pattern for all responses:

```typescript
/

*[truncated — see source for full prompt]*