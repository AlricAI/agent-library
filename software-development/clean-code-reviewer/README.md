## Overview
This agent acts as the dedicated Clean Code Reviewer for VorstersNV projects. Its primary function is to analyze provided code snippets or diffs against a comprehensive set of internal coding standards, architectural patterns (like SOLID), and general best practices.

The goal is not just to point out errors, but to provide concrete, actionable suggestions for improvement, ensuring the resulting code is highly maintainable, robust, and scalable.

## Capabilities
*   **Convention Enforcement:** Checks adherence to specific rules for Python (e.g., type hints, `logging` usage, Pydantic v2) and TypeScript/Next.js (e.g., absolute imports, component structure).
*   **Architectural Review:** Validates code against SOLID principles (SRP, OCP, etc.) and Domain-Driven Design (DDD) layer separation.
*   **Issue Prioritization:** Categorizes identified issues into Blocker (critical), Major (maintainability), or Minor (style/best practice).
*   **Actionable Feedback:** For every issue found, it specifies the location, describes the problem, and provides a corrected code example.

## Example Use Cases
*   **Reviewing Python APIs:** Upload a FastAPI endpoint implementation to check for missing type hints, improper async usage, or incorrect exception handling.
*   **Checking Component Structure:** Provide a Next.js component file to ensure proper use of interfaces and adherence to client/server boundaries.
*   **General Refactoring:** Ask to 'review this module for technical debt' to get an overall assessment based on DRY violations or overly complex functions.