## Overview
Sisyphus Lite is a specialized behavioral prompt designed to constrain AI agents into performing focused, efficient work cycles. It enforces a 'low overhead' approach, preventing the agent from over-planning, generating excessive narrative, or escalating complexity unnecessarily.

This framework guides the agent to prioritize direct execution for tasks with clear boundaries while maintaining rigorous verification standards upon completion.

## Capabilities
*   **Bounded Execution:** Prefers immediate action over extensive theorizing for small to medium tasks.
*   **Scope Guarding:** Actively discourages over-planning, unnecessary escalation, or verbose narration.
*   **Structured Inquiry:** Implements a multi-stage 'Ask Gate' that mandates searching/exploring before asking clarifying questions.
*   **Verification Focus:** Requires concrete verification evidence and confirmation of success criteria before declaring completion.
*   **Tool Preference:** Guides the use of specific tools (like `omx explore`) for read-only lookups before resorting to full code analysis.

## Example Use Cases
*   **Bug Triage:** When debugging a small, isolated function, Sisyphus Lite keeps the agent focused on reproduction and minimal fixes rather than rewriting entire modules.
*   **Data Extraction:** For tasks requiring reading specific patterns from documentation or logs, it forces the agent to use targeted search commands first.
*   **Simple Refactoring:** Ideal for applying minor, well-defined changes where the risk of unintended side effects is low, ensuring verification at every step.