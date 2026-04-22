# Deep Linking V2p0 Implementation Plan

> **Scope**: Tool-side Deep Linking v2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deep Linking v2.0 Implementation Plan

**Scope**: Tool-side Deep Linking v2.0. Given a platform launch with
`message_type` = `LtiDeepLinkingRequest`, the tool can present a content
selection UI, build content items, sign a response JWT, and redirect the
user back to the platform with the selected items.

**Spec references**:
- `[DL §X]` → LTI Deep Linking v2.0
  (https://www.imsglobal.org/spec/lti-dl/v2p0/)
- `[Sec §X]` → 1EdTech Security Framework v1.0
  (https://www.imsglobal.org/spec/security/v1p0/)
- `[Core §X]` → LTI Core Specification v1.3
  (https://www.imsglobal.org/spec/lti/v1p3/)
- `[AGS §X]` → LTI Assignment and Grade Services v2.0
  (https://www.imsglobal.org/spec/lti-ags/v2p0/)

**Prerequisites**: LTI 1.3 Core launch flow (already implemented). The
`DeepLinkingSettings` claim is already parsed from launch JWTs
(`Ltix.LaunchClaims.DeepLinkingSettings`). JWK management
(`Ltix.JWK`), Registration with `tool_jwk`, and the OAuth infrastructure
are all in place.

**Approach**: TDD. Each module is developed test-first. All modules use
`Zoi` for schema validation, struct construction, and documentation
generation.

---

## 1. How Deep Linking Differs from Advantage Services

Deep Linking is fundamentally different from NRPS and AGS:

| Aspect | NRPS / AGS | Deep Linking |
|--------|-----------|--------------|
| Flow | OAuth 2.0 client credentials → HTTP API calls | OIDC message flow → JWT form POST response |
| Direction | Tool calls platform API | Tool redirects user back to platform |
| Authentication | Bearer token | Signed JWT (tool's private key) |
| Data exchange | JSON API responses | Content items embedded in JWT |
| Timing | After launch, asynchronous | During launch, synchronous |

Deep Linking does NOT implement the `AdvantageService` behaviour. It does
not use OAuth tokens, does not make HTTP API calls, and does not interact
with `Ltix.OAuth.Client`. Instead, it extends the existing OIDC launch
flow to accept a second message type (`LtiDeepLinking

*[truncated — see source for full prompt]*