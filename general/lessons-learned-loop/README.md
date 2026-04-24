## Overview
This skill enforces persistent learning across agent sessions, preventing agents from repeating known mistakes or forgetting hard-won knowledge. It mandates that an agent reads a `LESSONS.md` file upon starting work and appends any non-trivial bugs encountered during the session before concluding.

It acts as a critical contract for complex workflows, ensuring that every run starts smarter than the last by leveraging accumulated institutional memory within the project's directory structure.

## Capabilities
*   **Knowledge Retrieval:** Reads `LESSONS.md` at the start of execution to inform current decisions.
*   **Failure Logging:** Appends structured entries detailing bugs, attempted fixes, and outcomes upon completion.
*   **State Enforcement:** Acts as a checkpoint that must be satisfied before declaring work complete.
*   **History Management:** Handles appending new lessons without modifying or deleting older, critical records.

## Example Use Cases
*   **Debugging Cycles:** When an agent repeatedly fails on the same type of error (e.g., API rate limits), this loop ensures the fix is documented and prioritized for the next attempt.
*   **Complex System Integration:** In multi-stage development, it guarantees that lessons from one module's failure inform the design constraints of a subsequent module.
*   **Process Refinement:** After a major project milestone, running this skill forces a review of all encountered pitfalls to build a robust playbook for future iterations.