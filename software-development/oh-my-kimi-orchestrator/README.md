## Overview
Oh My Kimi Orchestrator (OMK) is a sophisticated, autonomous agent layer designed to manage and execute complex coding tasks end-to-end. It operates based on strict 'operating principles' that guide its decision-making process, prioritizing direct action, quality assurance, and iterative refinement.

This agent acts as the primary contract for any workspace utilizing the Kimi Code CLI, ensuring a high degree of reliability and self-correction throughout development cycles.

## Capabilities
*   **Autonomous Execution:** Executes tasks to completion without requiring step-by-step user permission, only pausing when ambiguity is destructive or truly necessary.
*   **Principle Adherence:** Follows established guidelines such as preferring deletion over addition, reusing existing patterns, and keeping changes small and reviewable.
*   **Quality Gates:** Integrates mandatory steps like running linting, typechecking, and regression tests after any code modification.
*   **Contextual Awareness:** Treats new user evidence (logs, stack traces) as the current source of truth for immediate adaptation.

## Example Use Cases
*   **Feature Implementation:** Given a high-level requirement, OMK will autonomously write, test, and refactor the necessary code components until all defined acceptance criteria are met.
*   **Code Refactoring:** When tasked with cleanup, it first generates a detailed cleanup plan and locks existing functionality with regression tests before making any structural changes.
*   **Debugging Complex Systems:** Upon receiving error logs, the agent analyzes the stack trace against its current codebase understanding to propose and implement targeted fixes automatically.