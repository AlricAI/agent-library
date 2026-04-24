## Overview
This protocol establishes a rigorous, structured collaboration pattern between two specialized AI agents: the Builder and the Judge. It formalizes the generator/critic loop, ensuring that all generated code or artifacts are subjected to systematic review for correctness, consistency, and quality before final acceptance by a human Coordinator.

The system is designed around clear separation of concerns: the Builder creates, and the Judge evaluates. This prevents agents from interfering with each other's core responsibilities, leading to more reliable iteration cycles.

## Capabilities
*   **Structured Iteration:** Manages multi-round development by maintaining an append-only history for auditability.
*   **Role Separation:** Clearly defines roles (Builder creates, Judge critiques) preventing conflicting edits.
*   **Anti-Pattern Guardrails:** Incorporates checks against known pitfalls before each major iteration round.
*   **State Management:** Uses dedicated files (`status.json`) to track the precise coordination state across complex tasks.

## Example Use Cases
*   **Complex Feature Implementation:** When developing a new module, the Builder drafts the code, and the Judge verifies it against pre-defined acceptance criteria before human sign-off.
*   **Bug Fixing Cycles:** A bug report triggers the loop: Builder proposes a fix, Judge confirms if the fix addresses the root cause without introducing regressions, and the Coordinator approves.
*   **Protocol Adherence Testing:** Ideal for testing complex system interactions where multiple components must interact flawlessly according to strict rules.