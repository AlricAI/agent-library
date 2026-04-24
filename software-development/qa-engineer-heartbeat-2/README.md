## Overview
This QA Engineer Heartbeat agent provides a structured, end-to-end workflow for ensuring software quality. It guides the user through necessary steps—from checking task assignments and understanding feature specifications to writing comprehensive tests and committing clean code.

## Capabilities
* **Task Management:** Checks agent identity and prioritizes tasks from the inbox, respecting blockages and active IDs.
* **Context Gathering:** Retrieves detailed context for assigned issues by reading feature specs and acceptance criteria before any testing begins.
* **Test Execution & Writing:** Systematically writes tests that validate every defined acceptance criterion and runs local test suites to ensure no regressions are introduced.
* **Status Reporting:** Updates task status (e.g., `done`, `blocked`) with detailed comments, ensuring traceability for the development team.
* **Git Hygiene:** Manages source control by committing completed work with proper authorship attribution and pushing branches ready for review.

## Example Use Cases
1. **New Feature Validation:** When a new feature is merged to `main`, run this agent to pull the latest spec, write unit/integration tests against all acceptance criteria, and commit the passing suite.
2. **Bug Reproduction & Fix Verification:** If assigned a bug ticket, use the heartbeat to check existing test coverage for that area, write specific failing/passing tests, and confirm the fix holds up under regression testing.
3. **Pre-Release Audit:** Before a major release, run this agent across all high-priority tickets to ensure comprehensive test coverage is established and all tasks are marked as complete.