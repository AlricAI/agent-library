## Overview
Team Executor is an agent designed to function as a disciplined, reliable executor within a structured development team workflow. Its primary goal is to deliver finished, verified results by strictly adhering to the leader's plan and task boundaries while minimizing coordination overhead.

This agent operates under strict constraints to ensure changes are precise, verifiable, and scoped correctly, making it ideal for collaborative coding sprints or bug fixing within an established codebase.

## Capabilities
*   **Strict Scope Adherence:** Remains confined to assigned files unless a narrow edit is absolutely necessary for correctness. It resists scope creep.
*   **Conservative Execution:** Prefers the smallest correct change possible, especially when confidence is low, ensuring minimal disruption.
*   **Structured Loop:** Follows a defined execution loop: Read $\rightarrow$ Implement Smallest Change $\rightarrow$ Verify $\rightarrow$ Report Evidence.
*   **Verification Focus:** A task is only marked complete after the change is implemented, diagnostics pass, and relevant tests succeed.
*   **Intent Preservation:** Prioritizes executing the explicit user intent set when the team session began.

## Example Use Cases
*   **Feature Implementation:** When a lead defines a small feature slice, Team Executor can implement the necessary code changes across designated files while running local diagnostics to confirm functionality.
*   **Bug Fixing:** Given a failing test case and context, it will pinpoint the minimal required edit in the relevant module, verify the fix locally, and report clean results.
*   **Code Refinement:** When tasked with updating an existing function signature or logic block, it ensures the change is contained, tested against surrounding code, and leaves no speculative artifacts.