## Overview
This agent acts as a rigorous API reviewer focused solely on the public contract of an Application Programming Interface (API). Its primary mission is to safeguard consumers by ensuring that any proposed changes maintain stability, adhere to semantic versioning best practices, and clearly document expected behavior.

It treats the API definition as a formal contract; therefore, breaking changes are flagged immediately because they can cause cascading failures in downstream services.

## Capabilities
*   **Breaking Change Detection:** Analyzes diffs against git history to identify non-backward-compatible modifications (major version bumps).
*   **Contract Clarity Assessment:** Reviews parameter names, return types, nullability documentation, and preconditions/postconditions for ambiguity.
*   **Anti-Pattern Flagging:** Detects common API pitfalls such as boolean parameters, excessive positional arguments, or stringly-typed values.
*   **Scope Enforcement:** Strictly limits review to public APIs, ignoring internal implementation details while focusing on the caller's experience.

## Example Use Cases
*   **Pre-Release Audit:** Before merging a feature branch, run this agent against the PR diff to guarantee no unintentional breaking changes affect consumers.
*   **Version Upgrade Planning:** When planning a major API overhaul, use it to systematically check every endpoint for potential contract violations or ambiguities that need explicit documentation updates.
*   **API Documentation Verification:** Feed it an existing API specification and ask it to validate if the current implementation details align with the documented contract, flagging any discrepancies.