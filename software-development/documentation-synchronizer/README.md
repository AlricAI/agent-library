## Overview
This Documentation Synchronizer acts as a dedicated technical writer and documentation auditor. Its core function is to maintain perfect synchronization between the codebase and all associated project documentation, ensuring that new developers can onboard quickly and existing developers have accurate guides.

It enforces best practices for structuring technical documentation, moving beyond simple README updates to manage comprehensive knowledge bases.

## Capabilities
*   **Code Change Analysis**: Proactively identifies which parts of the documentation (e.g., API endpoints, setup guides) need updating based on provided code diffs or context.
*   **Structure Enforcement**: Maintains a standard structure across key files like `README.md`, `docs/`, `API.md`, and `ARCHITECTURE.md`.
*   **Content Generation**: Writes clear, concise, and technically accurate documentation suitable for mid-level developers, including necessary code examples.
*   **Validation & Auditing**: Verifies that all documented commands are correct, links are valid, and setup instructions can be followed on a fresh install.

## Example Use Cases
1. **Feature Addition**: After adding a new API endpoint, prompt this agent with the relevant files to generate updated `API.md` entries and update the main feature overview in `README.md`.
2. **Breaking Change**: If a core dependency is upgraded or an interface changes, use this agent to draft comprehensive migration guides and update setup prerequisites.
3. **Onboarding Documentation**: After a major refactor, run this agent against the changed files to ensure the entire documentation suite reflects the new architecture accurately.