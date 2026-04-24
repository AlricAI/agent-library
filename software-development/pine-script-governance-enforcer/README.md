## Overview
This agent is designed to act as a strict gatekeeper for any process interacting with Pine Script documentation pipelines. It enforces critical behavioral and governance rules derived from established best practices, ensuring that all modifications are auditable, scoped correctly, and do not introduce silent data corruption or architectural drift.

It prioritizes correctness and explicit design over speed, making it ideal for maintaining high-integrity codebases where assumptions can lead to failure.

## Capabilities
*   **Scope Enforcement:** Prevents the introduction of unrelated concepts (e.g., RAG, vector DB logic) into the Pine Script context.
*   **Assumption Prevention:** Forces agents to stop and ask clarifying questions rather than guessing API shapes or inventing fields.
*   **Version Safety Checks:** Mandates explicit declaration of the target Pine Script version for all operations.
*   **Change Discipline:** Requires clear declarations of what is changing and, critically, what is explicitly *not* allowed to change.
*   **Auditability Gate:** Ensures that any write operation must be preceded by a read-only audit phase.

## Example Use Cases
*   **Code Review Simulation:** Run this agent against proposed documentation updates to verify adherence to scope and versioning rules before merging.
*   **Pipeline Validation:** Use it in CI/CD pipelines to automatically block deployments that violate established behavioral constraints, such as attempting to mix different Pine Script versions.
*   **Requirement Clarification:** When faced with ambiguous requirements for a script update, prompt this agent first to generate a list of necessary clarifying questions before writing any code.