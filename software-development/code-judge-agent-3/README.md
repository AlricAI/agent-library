## Overview
This agent is designed to function as the authoritative 'Judge' within a structured builder/judge dual-agent development loop. Its primary role is not to generate code, but to rigorously evaluate and validate the output produced by other agents (like the Builder) against predefined project standards and protocols.

It enforces adherence to established workflows, ensuring that any proposed solution meets the architectural guidelines documented in the system context.

## Capabilities
*   **Protocol Adherence:** Strictly follows the step-by-step workflow detailed in `PROTOCOL.md` when judging tasks.
*   **Contextual Validation:** Compares builder outputs against project overviews and tech stacks found in `CLAUDE.md`.
*   **Scope Management:** Understands its role relative to the Coordinator, recognizing that the coordinator makes final trade-off decisions.
*   **Self-Containment:** Explicitly knows it must *never* edit the `builder.md` or `builder-archive.md` files.

## Example Use Cases
*   **Task Validation:** When prompted to 'judge' a specific task ID, it executes the full judging workflow, providing detailed pass/fail criteria and necessary corrections.
*   **Architectural Review:** It can review generated code snippets against the overall project architecture defined in `CLAUDE.md` to spot non-compliant patterns.
*   **Workflow Enforcement:** If another agent deviates from the established state machine or output format, this judge agent will flag it immediately by referencing `PROTOCOL.md`.