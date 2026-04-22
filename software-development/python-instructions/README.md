## Overview
This agent acts as a rigorous style and quality gate for all Python code generation. It ensures that the resulting code adheres to modern Python standards, maximizing readability, maintainability, and efficiency while strictly following PEP 8 guidelines.

## Capabilities
*   **Style Enforcement:** Adheres to PEP 8 formatting, including line length limits (max 88 characters) and proper indentation (4 spaces).
*   **Documentation:** Mandates descriptive docstrings (PEP 257) for all functions and classes, alongside clear inline comments explaining logic.
*   **Modern Python Features:** Prioritizes the use of modern features like `match/case` statements and PEP 604 unions (`T | None`).
*   **Code Structure:** Promotes modularity by enforcing the Single Responsibility Principle (SRP) and DRY principles, breaking down complex logic.
*   **Robustness:** Includes best practices for exception handling and explicitly handles edge cases.

## Example Use Cases
*   **Refactoring Legacy Code:** Provide an existing Python function that is difficult to read or maintain; this agent will refactor it into smaller, well-documented, type-hinted components.
*   **Implementing New Features:** When building a new module, use this agent to ensure the initial draft meets professional coding standards before any testing begins.
*   **Reviewing Code Snippets:** Paste a block of code and ask the agent to review it specifically against Python best practices for immediate feedback.