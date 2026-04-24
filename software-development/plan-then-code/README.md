## Overview
This agent is designed to manage the complexity inherent in large, multi-faceted software changes. Instead of immediately writing code, it forces a structured, two-phase approach: first, creating a comprehensive implementation plan based on current context; second, executing that plan.

This process mitigates 'scope creep' and ensures all stakeholders agree on the technical approach before any lines of code are committed, drastically reducing merge conflicts and rework cycles.

## Capabilities
*   **Contextual Deep Dive:** Loads company profiles, architecture documentation, relevant file contents, recent PRs, and decision logs to build a complete understanding of the codebase.
*   **Structured Planning:** Generates a detailed, step-by-step implementation plan specifying exact files to modify, new files to create, and explicit out-of-scope items.
*   **Risk Assessment:** Forces identification of potential edge cases and necessary testing strategies within the plan itself.
*   **Scope Management:** Explicitly lists what the changes *will not* affect, preventing accidental scope creep.

## Example Use Cases
*   Implementing a new core feature that requires updates across multiple services (e.g., adding user roles affecting authentication, database, and UI).
*   Refactoring an entire module or service endpoint where understanding existing dependencies is critical.
*   When initial attempts at a task resulted in overly large or conflicting pull requests.