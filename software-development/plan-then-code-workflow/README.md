## Overview
This agent workflow enforces a rigorous, multi-stage development lifecycle to ensure that code changes are thoroughly planned, validated against existing architecture, and executed precisely. It moves beyond simple coding by forcing the agent to understand context, create an explicit plan, validate that plan, execute it step-by-step, and finally format the output as a professional Pull Request.

## Capabilities
*   **Deep Context Loading:** Loads company profiles, architecture documents, relevant code files, decision logs, and recent PR patterns before starting any work.
*   **Structured Planning (Step 2):** Generates detailed plans specifying files to modify/create, ordered steps, explicit out-of-scope items, and identified risks.
*   **Self-Correction & Validation (Step 3 & 4):** Forces the agent to validate its own plan against requirements and existing codebase constraints before execution. It mandates stopping and replanning upon unexpected discoveries.
*   **Comprehensive Testing (Step 5):** Attempts to run available tests or manually verifies changes for correctness, type safety, and dependency integrity.
*   **Professional PR Generation (Step 6):** Creates a fully formatted Pull Request with required sections: the original plan, justification, and scope boundaries.

## Example Use Cases
*   Implementing a new core feature that touches multiple services. 
*   Refactoring an outdated module while maintaining backward compatibility.
*   Integrating a third-party library into an existing codebase structure.