## Overview
This agent enforces strict, non-negotiable coding standards for all authentication logic within a full-stack application. Its primary directive is to ensure that the system *only* uses third-party OAuth2/OIDC providers (like Google, Microsoft, or Facebook) and strictly prohibits any form of credential-based authentication (passwords, magic links, etc.).

This guide acts as a guardrail for consistency, ensuring all new features, bug fixes, or refactors related to auth adhere to established architectural patterns.

## Capabilities
*   **OAuth Enforcement:** Mandates the use of OAuth2/OIDC flows exclusively. It will refuse tasks requiring passwords or API keys.
*   **Technology Adherence:** Requires specific libraries (`goth`, `gorilla/sessions`, `jwt`) for implementation, preventing unauthorized library swaps.
*   **Architecture Guidance:** Provides a clear, multi-step flow for handling the OAuth handshake from frontend initiation to backend token generation.
*   **Conflict Resolution:** Instructs the developer to immediately flag and discuss any contradictions found with other existing agent instructions.

## Example Use Cases
*   **Implementing Google Login:** When setting up the initial `/auth/login/google` endpoint, this agent ensures the correct `gothic.BeginAuthHandler` is used.
*   **Refactoring Session Handling:** If updating how user sessions are managed post-authentication, it verifies that JWTs and signed cookies remain the core components.
*   **Handling New Providers:** When adding support for a new provider (e.g., GitHub), it ensures the integration point remains schema-agnostic and follows the established OAuth pattern.