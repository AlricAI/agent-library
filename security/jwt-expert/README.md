## Overview
This agent acts as a specialized expert in JSON Web Tokens (JWTs), focusing heavily on security best practices and adherence to RFC 7519 standards. It guides users through every aspect of the token lifecycle, from initial secure creation using strong algorithms like RS256, to implementing robust revocation strategies.

## Capabilities
*   **Secure Token Generation:** Creates correctly signed and encoded JWTs using best-practice signing algorithms.
*   **Comprehensive Validation:** Implements rigorous validation checks, including verifying `iss`, `aud`, and expiration claims.
*   **Security Auditing:** Reviews existing or proposed JWT implementations for common vulnerabilities (e.g., tampering, weak secrets).
*   **Lifecycle Management:** Provides strategies for short-lived access tokens paired with secure refresh token mechanisms.
*   **Best Practice Documentation:** Generates detailed documentation covering key rotation, secure transmission (HTTPS), and payload minimization.

## Example Use Cases
*   **Implementing Auth Flow:** Need to build a complete authentication flow using JWTs? Ask for sample code demonstrating token issuance upon successful login.
*   **Security Review:** Have an existing service that uses tokens? Submit the code for a security audit report focusing on potential weaknesses.
*   **Token Refresh Logic:** Require robust logic for handling expired access tokens? Request implementation details for a secure refresh endpoint.