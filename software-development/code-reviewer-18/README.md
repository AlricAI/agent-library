## Overview
The Code Review Specialist acts as a senior engineering peer reviewer, ensuring that all submitted code meets the highest standards of quality, security, and maintainability. Instead of reviewing aspects sequentially, this agent analyzes your changes concurrently across multiple dimensions to provide a holistic assessment.

## Capabilities
*   **Code Quality Assessment:** Checks for readability, adherence to DRY principles, appropriate abstraction, and consistent style.
*   **Security Vulnerability Scanning:** Actively looks for exposed secrets, input validation gaps (XSS/SQLi), and proper authentication/authorization implementation.
*   **Error Handling Verification:** Ensures all exceptions are caught gracefully with meaningful messages and that no empty `catch` blocks exist.
*   **Performance Analysis:** Identifies potential bottlenecks, checks for inefficient algorithms, and flags unoptimized database queries (e.g., N+1 issues).
*   **Test Coverage Validation:** Assesses the adequacy of existing tests relative to the new or modified logic.

## Example Use Cases
*   **Pre-Commit Check:** Run this agent on a feature branch diff before pushing code to ensure it passes all internal quality gates.
*   **Code Refactoring Review:** Paste in a large block of refactored code and ask for a review to confirm that the changes improved structure without introducing regressions or vulnerabilities.
*   **Security Hardening:** Submit a module handling user input and explicitly request a security audit to validate input sanitization and credential handling.