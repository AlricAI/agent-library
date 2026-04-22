# Core V1p3 Implementation Plan

> **Scope**: Tool-side LTI 1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Ltix v0.1.0 — LTI 1.3 Core (Tool Side) Implementation Plan

**Scope**: Tool-side LTI 1.3 Core launch flow + claim parsing (including Advantage
service claim structs for AGS, NRPS, and Deep Linking endpoints). No platform side.
No Advantage service *API calls* — just parsing the claims platforms send in launches.

**Guiding principle**: Every line of every function must clearly communicate which
passage of the spec it implements. Spec references use the format:

- `[Core §X.Y.Z]` → LTI 1.3 Core Specification (https://www.imsglobal.org/spec/lti/v1p3/)
- `[Sec §X.Y.Z]` → 1EdTech Security Framework v1.0 (https://www.imsglobal.org/spec/security/v1p0/)
- `[Cert §X.Y.Z]` → LTI Advantage Conformance Certification Guide (https://www.imsglobal.org/spec/lti/v1p3/cert)

**Approach**: TDD, driven by the Certification Guide test cases [Cert §6].
Each module is developed test-first, with tests named after the conformance
scenario they cover.

---

## 1. Project Bootstrap

### 1.1 Mix Project Setup

```
mix new .
```

**Dependencies** (minimal, no framework coupling):

| Dependency | Purpose | Spec basis |
|---|---|---|
| `jose` | JWT/JWS/JWK (RS256 signing & verification) | [Sec §5.1.2] ID Token is a JWT; [Sec §5.1.3] RS256 verification; [Sec §6.1] RSA keys |
| `req` | HTTP client for JWKS fetching (testable via `Req.Test`) | [Sec §6.3] Key Set URL — tool fetches platform public keys from JWKS endpoint |
| `splode` | Structured, composable error types (Ash-compatible) | Rich error reporting |
| `plug` (optional) | Request/response interface for convenience wrappers | [Sec §5.1.1.3] Authentication response via form_post — optional, not required for core API |

JSON encoding/decoding uses the built-in `JSON` module (OTP 27+). No `jason` dependency needed.

No Ecto, no Phoenix, no database. The library is storage-agnostic — callers
provide configuration and implement a behaviour for state persistence (nonces,
registrations).

### 1.2 Directory Structure

```
lib/
  ltix.ex         

*[truncated — see source for full prompt]*