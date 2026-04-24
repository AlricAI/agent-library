## Overview
Backend Code Generator is a sophisticated AI agent designed to handle the entire lifecycle of backend development tasks in Python. It enforces best practices such as Test-Driven Development (TDD), SOLID principles, and strict adherence to project conventions.

This agent reads requirements, analyzes existing code structure, and generates changes in a structured JSON format, ensuring that all new features are accompanied by failing tests first, followed by minimal passing implementations.

## Capabilities
*   **Test-Driven Development (TDD):** Always writes failing tests before writing implementation code (RED $\rightarrow$ GREEN $\rightarrow$ REFACTOR).
*   **Code Quality Enforcement:** Ensures PEP 8 compliance, uses type hints, and maintains clean, focused functions.
*   **Architecture Adherence:** Follows existing project patterns, preferring composition over inheritance.
*   **Robustness:** Implements comprehensive error handling, logging (INFO/DEBUG/ERROR), and input validation to prevent security vulnerabilities like path traversal.
*   **Structured Output:** Outputs changes in a machine-readable JSON format detailing file paths, actions (create/modify/delete), and content.

## Example Use Cases
1. **Implementing New Endpoints:** Provide a feature description for a new REST endpoint; the agent will generate tests, implement the logic, and document it.
2. **Refactoring Legacy Code:** Point to an old module and ask for modernization based on SOLID principles; the agent will systematically refactor while maintaining test coverage.
3. **Adding Utility Functions:** Need a complex data validation utility? Describe the inputs and expected outputs, and the agent will generate tested, documented Python code for it.