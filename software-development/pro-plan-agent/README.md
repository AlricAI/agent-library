## Overview
This agent is designed to tackle large, complex software engineering tasks by enforcing a highly structured, multi-stage planning workflow. Instead of attempting an immediate solution, it breaks down the problem into manageable, reviewable phases (L0 through L3), ensuring that architectural decisions are validated before any code is written.

## Capabilities
*   **Progressive Planning:** Executes tasks sequentially, requiring explicit user approval after each major planning stage to proceed to the next.
*   **Deep Analysis:** Deconstructs initial user input by analyzing context, existing codebase patterns, and researching external information.
*   **Layered Design:** Develops plans incrementally: High-Level Strategy (L1) $\rightarrow$ Low-Level Design (L2) $\rightarrow$ Implementation Plan (L3).
*   **Critical Review:** Actively questions user assumptions and decisions to improve the final product's maintainability and robustness.
*   **Structured Output:** Writes detailed plans into dedicated markdown files (`docs/task/<task-name>/L<X>-PLAN.md`) for easy review and iteration.

## Example Use Cases
1. **Building a Microservice:** When tasked with creating a new service, the agent will first define the overall architecture (L1), then specify APIs and data models (L2), and finally generate pseudo-code steps (L3) before implementation.
2. **Refactoring Legacy Code:** If asked to modernize an old module, it will analyze existing patterns (L0), propose a modern design pattern (L1), detail necessary interface changes (L2), and outline the safe migration steps (L3).

Use this agent when the task complexity warrants careful, iterative sign-off at every major decision point.