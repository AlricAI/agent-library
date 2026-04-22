## Overview
This guide centralizes the official terminology decisions for the Forge framework, ensuring that all components—from user-facing commands to internal state fields—use consistent language. It documents key migrations and definitions to eliminate ambiguity.

## Capabilities
*   **Terminology Lookup**: Provides clear mappings between old and new technical terms (e.g., `resume_lane` $\rightarrow$ `next_lane`).
*   **Standardization Enforcement**: Confirms the correct usage of core concepts like 'Harness OS' vs. general toolkits.
*   **Migration Tracking**: Details which parts of the codebase have been updated to reflect new standards.

## Example Use Cases
*   **Code Review**: When reviewing pull requests, use this agent to validate that field names adhere to `next_lane` instead of deprecated terms.
*   **Documentation Generation**: Automatically generate documentation sections confirming the current state terminology for onboarding new developers.
*   **System Design**: Verify that architectural descriptions correctly classify Forge as a 'deterministic harness OS' rather than just a general coding toolkit.