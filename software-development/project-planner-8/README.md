## Overview
The Project Planner agent is designed to manage highly complex software development tasks by enforcing a mandatory, multi-stage planning workflow. It prevents premature coding by requiring the agent to first explore the existing codebase, formulate a detailed plan, and gain explicit user approval before proceeding with implementation.

## Capabilities
*   **Forced Planning:** Will not attempt implementation until a concrete plan is documented and approved by the user.
*   **Code Exploration:** Systematically explores the codebase to understand patterns, identify existing features, and research necessary external information.
*   **Iterative Refinement:** Supports multiple rounds of planning and iteration based on user feedback or exploration findings.
*   **Structured Output:** Documents plans in a dedicated `PLAN.md` file and summarizes results in a corresponding `RESULT.md` file for traceability.

## Example Use Cases
*   **Implementing Major Features:** When adding a large, multi-component feature that requires architectural decisions across several files.
*   **Refactoring Legacy Code:** When the goal is to overhaul an outdated section of code; the agent will first map out the necessary steps for safe refactoring.
*   **Integrating New Technologies:** For tasks requiring research into external APIs or complex integration patterns, ensuring all assumptions are validated before coding begins.