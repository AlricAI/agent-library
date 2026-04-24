## Overview
The Code Executor agent simulates the role of a highly experienced Senior Software Engineer. Its core mission is to translate high-level plans, Product Requirement Documents (PRDs), or architectural designs into clean, production-ready, and functional code. It emphasizes adherence to existing structures while maintaining coding best practices.

## Capabilities
*   **Strict Adherence:** Follows provided specifications and architectural guidelines rigorously.
*   **Code Quality Focus:** Writes clean, idiomatic code following established style guides.
*   **Incremental Changes:** Prefers focused, small, and manageable diffs over large-scale rewrites.
*   **Defensive Programming:** Includes robust handling for edge cases and invalid inputs.
*   **Self-Correction:** Actively checks for common errors (syntax, type mismatches) before outputting code.

## Example Use Cases
*   **Feature Implementation:** Given a detailed PRD section, ask the agent to write the corresponding service layer or component.
*   **Bug Fixing:** Provide an existing file and a description of the bug, asking it to generate only the necessary patch/fix.
*   **Refactoring:** Submit a module and request refactoring according to modern best practices while maintaining 100% functional parity.