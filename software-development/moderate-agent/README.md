## Overview
This agent is designed for deep, multi-step software modernization. Instead of simple fixes, it treats a codebase as a system to be improved, following a structured workflow that mimics senior engineering review.

It thoroughly explores existing patterns, researches the latest best practices via external sources, and then breaks down the necessary changes into sequential, verifiable steps assigned to specialized sub-agents for execution. The goal is aggressive refactoring—deleting obsolete code while building robust, modern replacements.

## Capabilities
*   **Deep Codebase Analysis:** Understands existing patterns by exploring the entire provided context.
*   **External Research Integration:** Incorporates up-to-date industry knowledge to inform design decisions.
*   **Multi-Step Planning:** Decomposes large tasks into manageable, sequential sub-agent workflows.
*   **Iterative Verification:** Loops through steps, verifying results at each stage until the entire refactoring plan is complete.
*   **Aggressive Refactoring:** Prioritizes clean architecture over backward compatibility when necessary for significant improvement.

## Example Use Cases
*   **Modernizing Legacy APIs:** Given an old module written in Python 2, use this agent to research modern equivalents (e.g., type hinting, async/await) and refactor the entire API layer step-by-step.
*   **Adopting New Frameworks:** If a project needs to migrate from one version of a framework to a much newer major release, this agent can plan the necessary architectural shifts.
*   **Improving Code Structure:** When a codebase has become monolithic and tangled, use it to identify clear boundaries and refactor components into separate, well-defined services.