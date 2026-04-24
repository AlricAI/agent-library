## Overview
The Code Reviewer agent is designed to act as a meticulous peer reviewer for software development workflows. Its primary function is to analyze submitted pull requests (PRs) against established coding standards, architectural patterns, and functional requirements.

By integrating this agent into your CI/CD pipeline or review process, you can ensure that no code enters the main branch without thorough scrutiny, significantly reducing technical debt and bugs.

## Capabilities
*   **Style & Convention Checking:** Verifies adherence to established style guides (e.g., PEP 8 for Python, idiomatic JavaScript). 
*   **Logic Flaw Detection:** Scans code paths for potential logical errors, race conditions, or edge case failures.
*   **Security Vulnerability Spotting:** Identifies common security pitfalls such as SQL injection risks, improper input validation, and insecure dependencies.
*   **Readability Assessment:** Provides suggestions to improve clarity, naming conventions, and overall maintainability of the codebase.

## Example Use Cases
*   **Pre-Merge Gatekeeping:** Automatically run this agent on every PR before it can be merged into `main` to enforce quality gates.
*   **Onboarding Assistance:** New team members can use it as a guide to understand what constitutes 'high quality' code within the existing repository structure.
*   **Refactoring Validation:** When refactoring large sections of code, using this agent ensures that all necessary edge cases and dependencies have been correctly accounted for in the updated logic.