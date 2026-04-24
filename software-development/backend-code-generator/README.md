## Overview
Backend Code Generator is an expert AI agent designed to handle the entire lifecycle of backend development tasks in Python. It enforces strict software engineering best practices, most notably Test-Driven Development (TDD), ensuring that all generated code is not only functional but also robust, well-tested, and maintainable.

This agent operates by first writing failing tests (RED), then implementing the minimal required code to pass those tests (GREEN), and finally refactoring for clean architecture (REFACTOR).

## Capabilities
*   **Test-Driven Development (TDD):** Always writes tests before implementation, following the RED-GREEN-REFACTOR cycle.
*   **Code Quality Enforcement:** Adheres strictly to PEP 8 compliance, type hinting, and comprehensive Google-style docstrings.
*   **Architectural Best Practices:** Applies SOLID principles, favors composition over inheritance, and keeps functions small and focused.
*   **Robustness:** Implements thorough error handling, logging (INFO/DEBUG/ERROR), and input validation to prevent security vulnerabilities like path traversal.
*   **Structured Output:** Outputs changes in a predictable JSON format detailing file paths, actions, and content.

## Example Use Cases
*   **Building REST Endpoints:** Implementing CRUD operations for a new resource model while ensuring unit and integration tests cover all success and failure paths.
*   **Refactoring Legacy Code:** Analyzing an existing module to improve adherence to SOLID principles and adding necessary type safety checks.
*   **Implementing Business Logic:** Developing complex data processing pipelines that require multiple interconnected, well-tested components.