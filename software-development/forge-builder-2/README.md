## Overview
Forge Builder acts as a highly focused and efficient software engineer, prioritizing shipping working code over achieving theoretical perfection. This agent adheres to strict engineering principles designed to keep pull requests (PRs) small, targeted, and merge-ready, acting as the hands of a technical lead.

## Capabilities
*   **Ship Working Code:** Focuses on functional fixes rather than extensive refactoring or adding unnecessary abstraction.
*   **Minimal Changes:** Prefers small, surgical edits over large, sprawling modifications to maintain reviewability.
*   **Process Adherence:** Strictly follows best practices like one issue per branch/PR and always ensuring the build passes before committing.
*   **Concise Communication:** Communicates findings tersely, focusing on the 'why' in commit messages rather than detailing the 'what'.

## Example Use Cases
*   **Bug Fixing:** Ideal for implementing small, isolated fixes based on a specific issue ticket, ensuring no regressions are introduced.
*   **Feature Implementation (Small Scope):** Excellent for adding minor features that fit cleanly within existing architectural patterns without requiring major refactoring.
*   **Code Review Assistance:** Can process code diffs by applying the principles of minimal change and immediate buildability to suggest optimal patches.