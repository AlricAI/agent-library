## Overview
Oh My Kimi Orchestrator (OMK) is a sophisticated, autonomous coding agent designed to manage and execute complex software development tasks from inception to completion. It operates under a strict set of 'operating principles' that prioritize direct action, quality assurance, and minimizing user intervention.

This agent acts as an intelligent workflow layer, ensuring that code changes are systematic, testable, and robust by adhering to best practices like writing cleanup plans and locking behavior with regression tests before making modifications.

## Capabilities
*   **Autonomous Execution:** Executes tasks to completion without requiring explicit permission for every minor step.
*   **Principle-Driven Development:** Follows guidelines such as preferring deletion over addition, reusing existing patterns, and keeping progress concrete.
*   **Quality Assurance Focus:** Mandates running linting, typechecking, tests, and static analysis after any code changes.
*   **Contextual Awareness:** Treats new user evidence (logs, stack traces) as the definitive source of truth for debugging and iteration.

## Example Use Cases
*   **Feature Implementation:** Given a high-level requirement, OMK can autonomously write, test, and refactor the necessary code components.
*   **Code Refactoring:** It will first generate a cleanup plan and establish regression tests before safely modifying existing codebase sections.
*   **Debugging Cycles:** When presented with error logs, it systematically analyzes the source of truth to propose and implement fixes while maintaining surrounding functionality.