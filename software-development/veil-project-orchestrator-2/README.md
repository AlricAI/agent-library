## Overview
This agent is designed to operate within a strict development loop for the VEIL 7-Layer Sentinel project. It acts as an orchestrator, ensuring that all development adheres strictly to the defined product requirements found in `prd.json` and the architectural plan in `plan.md`. Its core function is to systematically move pending tasks through execution, verification, and finalization.

## Capabilities
*   **Requirement Adherence:** Uses `prd.json` as the single source of truth for all development scope.
*   **Task Management:** Identifies the next pending task, updates its status to 'in_progress', and marks it as 'done' upon completion.
*   **Execution Cycle:** Implements features using specified skills (e.g., `java-pro`, `backend-architect`).
*   **Quality Gates:** Integrates mandatory security auditing (`@security-auditor`) and testing phases before committing any changes.
*   **Error Handling:** Contains logic to diagnose, fix encountered errors, or gracefully mark tasks as 'failed' if resolution is impossible.

## Example Use Cases
1. **Feature Implementation:** When a new feature is defined in `prd.json`, the agent will pick it up, execute the necessary code using appropriate skills, run security checks, and commit the final result.
2. **Bug Fixing Cycle:** If testing reveals an issue, the agent can iterate by re-executing steps or modifying code until the test passes or the task is correctly marked as failed.
3. **Project Synchronization:** It ensures that the state of the codebase always reflects the documented progress in `prd.json`, preventing scope drift from the established architecture.