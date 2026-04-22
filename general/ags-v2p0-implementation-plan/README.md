# Ags V2p0 Implementation Plan

> **Scope**: Tool-side AGS v2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Assignment and Grade Services (AGS) v2.0 Implementation Plan

**Scope**: Tool-side AGS v2.0 service client. Given a successful LTI 1.3
launch that includes the AGS claim, the tool can manage line items
(gradebook columns), post scores, and read results from the platform's
gradebook.

**Spec references**:
- `[AGS §X]` → LTI Assignment and Grade Services v2.0
  (https://www.imsglobal.org/spec/lti-ags/v2p0/)
- `[Sec §X]` → 1EdTech Security Framework v1.0
  (https://www.imsglobal.org/spec/security/v1p0/)
- `[Core §X]` → LTI Core Specification v1.3
  (https://www.imsglobal.org/spec/lti/v1p3/)

**Prerequisites**: LTI 1.3 Core launch flow, OAuth 2.0 client credentials
(`Ltix.OAuth`), pagination (`Ltix.Pagination`), and the `AdvantageService`
behaviour are all implemented. The AGS endpoint claim
(`Ltix.LaunchClaims.AgsEndpoint`) is already parsed from launch JWTs.

**Approach**: TDD. Each module is developed test-first. The library remains
storage-agnostic and HTTP-client-agnostic (uses `Req` with testable stubs).
All new functions that accept keyword options use `NimbleOptions` for
validation, defaults, and documentation generation.

---

## 1. Service Overview

AGS is three services sharing a common endpoint claim and OAuth
infrastructure:

| Service | Direction | HTTP Methods | Media Type |
|---------|-----------|-------------|------------|
| **Line Item** | Read/Write | GET, POST (container); GET, PUT, DELETE (individual) | `application/vnd.ims.lis.v2.lineitem+json`, `application/vnd.ims.lis.v2.lineitemcontainer+json` |
| **Result** | Read-only | GET (container) | `application/vnd.ims.lis.v2.resultcontainer+json` |
| **Score** | Write-only | POST | `application/vnd.ims.lis.v1.score+json` |

**Scopes** [AGS §3.2, §3.3.2, §3.4.2]:

| Scope | Grants |
|-------|--------|
| `https://purl.imsglobal.org/spec/lti-ags/scope/lineitem` | Full line item CRUD |
| `https://purl.imsglobal.org/spec/lti-ags/scope/lineitem.readonly` | Read-only line item access |
| `https://purl.imsglo

*[truncated — see source for full prompt]*