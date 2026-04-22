# SECURITY IMPROVEMENTS

> This document describes the security enhancements made to AzureHayMaker's authentication and secret management systems (Issue #237).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Security Improvements - JWT Validation and Secret Management

This document describes the security enhancements made to AzureHayMaker's authentication and secret management systems (Issue #237).

## Overview

Two critical HIGH severity security vulnerabilities were addressed:
1. **Hardcoded VPN shared keys** in documentation (RESOLVED)
2. **JWT token validation without signature verification** (RESOLVED)

## JWT Signature Verification

### Problem
The previous implementation performed only basic JWT validation:
- Decoded tokens without verifying cryptographic signatures
- No protection against token forgery
- No replay attack prevention
- Manual base64 decoding (error-prone)
- Comment noted "For production, consider using python-jose" (line 101-102)

### Solution
Full cryptographic JWT validation using `python-jose[cryptography]>=3.3.0`:

```python
from jose import jwt
from jose.exceptions import ExpiredSignatureError, JWTClaimsError

# Validates signature using JWKS from Azure AD
claims = jwt.decode(
    token,
    jwks,
    algorithms=["RS256"],
    audience=valid_audiences,
    options={
        "verify_signature": True,
        "verify_aud": True,
        "verify_iat": True,
        "verify_exp": True,
        "verify_nbf": True,
        "verify_iss": True,
    }
)
```

### Key Features

#### 1. Cryptographic Signature Verification
- Fetches JWKS (JSON Web Key Set) from Azure AD
- Verifies RS256 signature using public keys
- Detects tampered or forged tokens
- Automatic key selection using `kid` header

#### 2. Token Replay Protection
- Tracks JTI (JWT ID) claims to prevent token reuse
- In-memory cache with automatic cleanup
- Expires cache entries based on token expiration
- Handles 10,000+ concurrent tokens

```python
# Replay detection
if jti in _jti_cache:
    raise TokenReplayError("Token has already been used")

_jti_cache[jti] = TokenRecord(jti=jti, exp=token_exp)
```

#### 3. JWKS Caching with TTL
- Caches JWKS for 1 hour (configurable)
- Lazy refresh

*[truncated — see source for full prompt]*