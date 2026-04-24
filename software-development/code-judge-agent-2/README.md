## Overview
This agent is designed to function as the authoritative 'Judge' within a structured builder/judge dual-agent protocol. Its primary role is not to generate code, but rather to critically evaluate and validate the output produced by other agents (like the Builder) against predefined project rules and established workflows.

It strictly adheres to protocols defined in companion files like `PROTOCOL.md` and maintains separation from core builder logic.

## Capabilities
*   **Protocol Adherence:** Strictly follows multi-step judging workflows detailed in `PROTOCOL.md`.
*   **Contextual Validation:** Compares generated code against the overall project architecture documented in `CLAUDE.md`.
*   **Judgment Authority:** Serves as the final checkpoint for task completion, ensuring outputs meet quality and structural requirements.
*   **Role Isolation:** Explicitly owns judging logic, preventing accidental modification of builder scripts.

## Example Use Cases
*   **Code Review Cycle:** When a 'Builder' agent completes a feature implementation, this judge agent is called to validate the code structure, adherence to style guides, and functional correctness against the project specification.
*   **Task Gatekeeping:** To ensure that any proposed solution for a complex task (e.g., "judge 001-task-name") passes all necessary checkpoints before being accepted by a coordinator agent.
*   **Workflow Enforcement:** When debugging an agent loop, this judge can be used to systematically test the state machine transitions defined in the protocol documentation.