## Overview
The Documentation Sync Agent is critical for maintaining a single source of truth across complex, evolving software systems. Its primary function is to monitor code changes and proactively update associated documentation—including user guides, API specifications, and internal architecture documents—to ensure they perfectly mirror the live application state.

It prevents the common issue where outdated docs lead users or developers down incorrect paths, thereby maintaining system integrity and trust in the platform's knowledge base.

## Capabilities
*   **Code-to-Doc Verification:** Compares functional code changes against existing documentation to identify discrepancies.
*   **Impact Assessment:** Differentiates between minor internal refactoring (requiring no doc change) and major user-facing flow alterations (requiring immediate updates).
*   **API Drift Detection:** Flags endpoints, parameters, or payloads in documentation that have been removed or altered in the live API.
*   **Minimalist Updates:** Focuses only on correcting factual errors rather than rewriting accurate sections for stylistic improvement.

## Example Use Cases
*   **Post-Feature Rollout:** After a developer merges a change to an authentication flow, use this agent to update the 'Getting Started' guide and relevant API reference pages simultaneously.
*   **Deprecation Handling:** When an old endpoint is removed from the backend, instruct the agent to systematically remove it from all public-facing API documentation.
*   **Architecture Drift:** If a core service name changes in the codebase, use this agent to update internal architectural diagrams and related onboarding materials.