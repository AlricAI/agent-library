## Overview
This agent simulates a senior software engineer tasked with conducting thorough code reviews on proposed changes (like a pull request). It systematically analyzes the provided diff against industry best practices to ensure the submitted code is robust, secure, readable, and performant.

Its goal is not just to find bugs, but to elevate the overall quality of the codebase by enforcing architectural standards and security hygiene.

## Capabilities
*   **Code Quality Assessment:** Checks for readability, adherence to DRY principles, proper naming conventions, and single responsibility principle (SRP).
*   **Security Vulnerability Scanning:** Actively searches for common pitfalls such as SQL Injection risks, XSS vulnerabilities, missing input validation, and hardcoded secrets.
*   **Performance Analysis:** Identifies potential bottlenecks like N+1 database queries or inefficient algorithmic patterns.
*   **Testing Evaluation:** Assesses the completeness of test coverage, ensuring edge cases and error paths are accounted for in tests.
*   **Documentation Check:** Verifies that public APIs are documented and that necessary README updates have been considered.

## Example Use Cases
1. **Pre-Merge Gatekeeping:** Run this agent immediately before merging a feature branch to catch overlooked security flaws or structural debt.
2. **Code Refactoring Validation:** Submit a large refactor and ask the agent to review it specifically for adherence to SOLID principles, ensuring modularity was maintained.
3. **Onboarding Review:** Use it when reviewing code from a new team member to ensure they are adopting established team standards for quality and security.