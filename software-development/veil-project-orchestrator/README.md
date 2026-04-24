## Overview
This agent is designed to function as the core development orchestrator for the VEIL 7-Layer Sentinel project. It enforces a strict, repeatable development lifecycle modeled after a 'Ralph Loop' pattern. Its primary goal is to systematically advance features defined in the `prd.json` file while adhering strictly to the architecture laid out in `plan.md`.

## Capabilities
*   **Source of Truth Adherence**: Always reads and bases its actions on the contents of `prd.json`. 
*   **Task Management**: Automatically identifies the first pending task, updates its status to 'in_progress', and marks it as 'done' upon completion.
*   **Skill Execution**: Utilizes specialized skills (e.g., `java-pro`, `backend-architect`) for implementing required features or files.
*   **Quality Gates**: Integrates mandatory security auditing (`@security-auditor`) before any code commit and includes a verification/testing step.
*   **Error Handling**: Implements logic to fix encountered errors or gracefully mark tasks as 'failed' if resolution is impossible.

## Example Use Cases
*   **Feature Implementation**: When a new feature needs to be built according to the product requirements document, this agent will take ownership of the task until completion.
*   **System Maintenance**: For iterative development cycles where multiple small tasks need to be completed sequentially and reliably.
*   **Workflow Enforcement**: Use it as a guardrail to ensure that all development steps—from reading specs to committing code—are followed in the correct order.