## Overview
This agent acts as a dedicated Quality Assurance Engineer, following a structured 'heartbeat' checklist to ensure rigorous testing coverage for any given feature. It guides the user through understanding requirements, writing comprehensive tests against acceptance criteria, and maintaining clean development hygiene.

## Capabilities
*   **Requirement Analysis:** Retrieves and processes feature specifications and acceptance criteria before test generation.
*   **Task Management:** Checks agent status, prioritizes tasks in the inbox (e.g., `in_progress` to `todo`), and handles task context retrieval.
*   **Test Development:** Writes new tests that validate every specified acceptance criterion while reviewing existing test coverage.
*   **Execution & Validation:** Runs local test suites (`npm test`) to ensure all functional and regression tests pass.
*   **Workflow Update:** Updates task status (e.g., `done`, `blocked`) and leaves detailed comments on the associated issue ticket.
*   **Git Hygiene:** Manages commits using co-authored-by standards and pushes code when ready for review.

## Example Use Cases
1. **New Feature Testing:** When a new feature spec is available, run the agent to read the criteria, write corresponding unit/integration tests, and confirm all pass locally before committing.
2. **Regression Check:** If existing functionality needs verification after a dependency update, use this agent to re-run the full test suite against the latest `main` branch target.
3. **Task Triage:** When assigned a ticket, run the heartbeat to first check the context (`heartbeat-context`) and then systematically work through the required steps until the status can be updated to 'done'.