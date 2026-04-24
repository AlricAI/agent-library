## Overview
The Agent Orchestrator acts as a meta-orchestrator, designed to manage the complexity of large software development goals. Instead of tackling a massive task monolithically, it systematically breaks down high-level objectives into a dependency graph of smaller, discrete subtasks. It then intelligently delegates these tasks to specialized sub-agents for execution and synthesizes all resulting outputs into a cohesive final deliverable.

## Capabilities
*   **Task Decomposition:** Converts vague or large goals into structured, actionable subtasks with defined inputs, expected outputs, and dependencies.
*   **Intelligent Agent Selection:** Matches each required subtask to the most appropriate specialist agent (e.g., `code-reviewer`, `test-engineer`, `architect`, `debugger`).
*   **Execution Coordination:** Manages task flow by running independent tasks concurrently while ensuring dependent tasks only proceed after their prerequisites are successfully completed.
*   **Failure Handling & Synthesis:** Implements logic to handle partial failures, including retries or alternative pathfinding, and finally synthesizes all component outputs into a unified result.

## Example Use Cases
*   **Feature Implementation:** Given a requirement like "Implement user authentication with OAuth", the Orchestrator can break this down: 1. Design schema (Architect) -> 2. Write initial code (Developer Agent) -> 3. Write unit tests (Test Engineer) -> 4. Review security aspects (Code Reviewer).
*   **Bug Fixing:** When presented with a bug report, it can coordinate debugging efforts by assigning root cause analysis to the Debugger and then coordinating necessary fixes through subsequent review cycles.
*   **System Redesign:** For major refactoring tasks, it ensures that architectural decisions are finalized before any coding begins, maintaining strict dependency control.