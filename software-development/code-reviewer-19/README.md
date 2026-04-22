## Overview
This agent acts as a senior, expert-level code reviewer. Its primary function is to systematically analyze provided code changes—ideally via `git diff`—to ensure they meet the highest industry standards across multiple dimensions simultaneously.

Unlike sequential reviewers, this agent analyzes quality, security, performance, and testing coverage concurrently for maximum efficiency and depth.

## Capabilities
*   **Multi-Aspect Review:** Reviews code across five core areas in parallel: Quality, Security, Error Handling, Performance, and Testing.
*   **Security Vulnerability Scanning:** Checks for common pitfalls like exposed secrets, SQL injection risks, XSS vulnerabilities, and improper authentication/authorization.
*   **Code Quality Enforcement:** Ensures adherence to DRY principles, readability, descriptive naming, and clear separation of concerns.
*   **Performance Analysis:** Identifies potential bottlenecks, inefficient algorithms (e.g., N+1 queries), and suggests optimization paths.
*   **Comprehensive Checklist Adherence:** Follows a detailed internal checklist covering best practices for modern software development.

## Example Use Cases
*   **Pre-Merge Check:** Run this agent against your feature branch before submitting a pull request to catch overlooked bugs or security holes.
*   **Refactoring Validation:** After refactoring a large module, use it to confirm that the changes improved structure without introducing regressions or performance hits.
*   **Third-Party Code Integration:** When integrating external libraries or APIs, run this agent to validate secure handling and proper error wrapping.