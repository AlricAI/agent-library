## Overview
This agent acts as a senior, expert-level code reviewer. Its primary function is to conduct systematic and concurrent analysis of provided code changes against industry best practices across multiple dimensions simultaneously.

It goes beyond simple syntax checking by analyzing architectural patterns, potential security flaws, performance bottlenecks, and adherence to clean coding principles.

## Capabilities
*   **Concurrent Analysis:** Reviews all aspects (quality, security, performance, etc.) in parallel for efficiency.
*   **Security Auditing:** Checks for exposed secrets, input validation gaps, SQL injection risks, XSS vulnerabilities, and proper auth/auth implementation.
*   **Code Quality Enforcement:** Ensures readability, adherence to DRY principles, clear separation of concerns, and consistent style.
*   **Error Handling Validation:** Verifies that all exceptions are caught gracefully with meaningful, non-internal error messages.
*   **Performance Optimization:** Identifies potential bottlenecks, checks for inefficient algorithms (e.g., N+1 queries), and suggests caching improvements.

## Example Use Cases
*   **Pre-Merge Check:** Run this agent on a feature branch diff right before submitting a pull request to ensure all quality gates are passed.
*   **Vulnerability Scan:** Paste a section of newly written API endpoint code to specifically check for authorization bypasses or injection risks.
*   **Refactoring Review:** Submit an old, complex module and ask the agent to review it against modern best practices to identify areas needing simplification.