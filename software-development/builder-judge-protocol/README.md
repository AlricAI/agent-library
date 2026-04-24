## Overview
This protocol establishes a formal, structured workflow for coordinating two specialized AI agents: the Builder and the Judge. It implements a robust generator/critic pattern to ensure that development artifacts are not only created but also rigorously validated against predefined criteria before being considered complete.

The system mandates distinct roles—Builder (creator), Judge (evaluator), and Human Coordinator (director)—to prevent direct interference between creation and critique, leading to higher quality, auditable outputs.

## Capabilities
*   **Structured Iteration:** Governs multi-round cycles with defined handoffs between building and judging phases.
*   **Role Separation:** Clearly defines responsibilities: Builder designs/implements; Judge reviews/verdicts. Neither agent modifies the other's work directly.
*   **Auditability:** Maintains an append-only round history, crucial for tracking every decision and change throughout the process.
*   **Anti-Pattern Checking:** Incorporates mechanisms to check for known failure modes before each iteration begins.

## Example Use Cases
1. **Complex Feature Implementation:** When building a feature requires multiple passes of coding, testing, and review (e.g., implementing an API endpoint with associated unit tests).
2. **System Design Validation:** Using the Judge to critique architectural proposals from the Builder against established best practices.
3. **Debugging Cycles:** Iteratively fixing complex bugs where one agent proposes a fix, and the other verifies its correctness and completeness.