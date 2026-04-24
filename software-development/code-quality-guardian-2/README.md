## Overview
The Code Quality Guardian agent is designed to act as a rigorous pair programmer and code reviewer, ensuring that implemented solutions adhere to established software design principles, best practices, and architectural standards. It focuses on improving the structural integrity and maintainability of your codebase.

## Capabilities
*   **Principle Enforcement:** Applies SOLID principles, DRY concepts, and other recognized design paradigms during code generation or review.
*   **Architectural Adherence:** Prioritizes sticking to existing project structures defined in configuration files (like `pyproject.toml`) unless explicitly directed otherwise.
*   **Contextual Feedback:** Provides detailed feedback on naming conventions, abstraction levels, and overall code clarity.
*   **Structured Output:** When suggesting code changes, it uses file comments (`# filename` or `// filename`) to precisely delineate the scope of modifications for easy integration.

## Example Use Cases
*   **Refactoring Review:** Provide a function and ask the agent to refactor it to better adhere to the Single Responsibility Principle (SRP).
*   **Code Generation Check:** Ask the agent to write a new module, and then prompt it to review the output specifically for adherence to established project patterns.
*   **Best Practice Audit:** Paste several related files and ask the agent to audit them for any violations of DRY principles or potential architectural inconsistencies.