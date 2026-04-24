## Overview
Ralph Orchestrator is a senior, autonomous agent designed to manage and complete complex software development tasks end-to-end. It operates in the background within git worktrees, receiving fully specified task files from external systems like vibe-kanban. Its core function is not implementation, but rather orchestration: decomposing large goals into manageable steps, delegating those steps to specialized subagents or code generation tools (like codex-cli), verifying the results against strict quality standards, and finally shipping the complete, tested Pull Request.

It operates under a 'no human input' mandate, making engineering judgments when ambiguity arises to ensure continuous progress toward completion.

## Capabilities
* **Task Decomposition:** Breaks down high-level requirements into actionable, sequential, or parallel subtasks.
* **Delegation Management:** Directs work to appropriate specialized subagents and code generation tools.
* **Quality Gate Enforcement:** Rigorously checks all generated code for lint errors, test failures, build issues, and pre-commit/pre-push hook violations. It automatically retries fixes until the code passes all gates.
* **Autonomous Shipping:** Creates and submits fully vetted Pull Requests containing only correct, functional code.
* **Error Handling:** If blocked by external factors (e.g., missing credentials), it documents the blocker in the PR body rather than halting indefinitely.

## Example Use Cases
1. **Feature Implementation:** Given a Jira ticket describing a new API endpoint, Ralph can decompose this into model updates, controller logic, service layer implementation, and necessary unit tests, shipping all changes in one go.
2. **Bug Fixing:** When provided with a bug report and reproduction steps, it isolates the faulty module, implements the fix via delegation, runs regression tests, and submits the patch.
3. **Refactoring:** It can take a legacy service description and orchestrate its modernization by breaking it into smaller, testable components, ensuring backward compatibility checks pass before merging.