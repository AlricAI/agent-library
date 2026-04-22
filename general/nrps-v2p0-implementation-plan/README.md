# Nrps V2p0 Implementation Plan

> **Scope**: Tool-side NRPS v2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Memberships — Names and Role Provisioning Services (NRPS) v2.0 Implementation Plan

**Scope**: Tool-side NRPS v2.0 service client. Given a successful LTI 1.3
launch that includes the NRPS claim, the tool can query the platform's
membership endpoint to retrieve context (course) memberships.

**Spec references**:
- `[NRPS §X]` → LTI Names and Role Provisioning Services v2.0
  (https://www.imsglobal.org/spec/lti-nrps/v2p0/)
- `[Sec §X]` → 1EdTech Security Framework v1.0
  (https://www.imsglobal.org/spec/security/v1p0/)
- `[Core §X]` → LTI Core Specification v1.3
  (https://www.imsglobal.org/spec/lti/v1p3/)

**Prerequisites**: LTI 1.3 Core launch flow (already implemented). The NRPS
endpoint claim (`Ltix.LaunchClaims.MembershipsEndpoint`) is already parsed
from launch JWTs (currently named `NrpsEndpoint` — will be renamed).

**Approach**: TDD. Each module is developed test-first. The library remains
storage-agnostic and HTTP-client-agnostic (uses `Req` with testable stubs).
All new functions that accept keyword options use `NimbleOptions` for
validation, defaults, and documentation generation. Existing functions
will be migrated to `NimbleOptions` in a separate effort.

---

## 1. OAuth 2.0 Client Credentials Token (Shared Infrastructure)

Before the memberships service can call the platform, it needs an access
token. LTI Advantage services use the OAuth 2.0 client credentials grant
with a signed JWT assertion per [Sec §4.1].

> [Sec §4.1]: "Consumers MUST use the OAuth 2.0 Client Credentials grant
> type." The client authenticates using a JWT signed with its private key
> [Sec §4.1.1].

This module is shared infrastructure — AGS, Deep Linking response, and any
future Advantage services will also use it.

### 1.1 `Ltix.OAuth.ClientCredentials` — Token Request

**Spec basis**: [Sec §4.1] OAuth 2.0 Client Credentials grant;
[Sec §4.1.1] Using JWTs for Client Authentication.

**Responsibilities**:
1. Build a JWT assertion signed with the tool's private key [Sec §4.1.1]
2

*[truncated — see source for full prompt]*