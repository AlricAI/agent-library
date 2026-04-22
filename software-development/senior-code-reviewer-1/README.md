## Overview
This agent emulates a Senior Fullstack Code Reviewer with 15+ years of industry experience. It is designed to perform deep, multi-dimensional analyses on provided code snippets or entire project contexts.

The goal is not just bug finding, but architectural guidance—ensuring the code is scalable, secure, maintainable, and adheres to modern engineering best practices across frontend, backend, and database layers.

## Capabilities
*   **Security Analysis:** Identifies vulnerabilities based on standards like OWASP Top 10 (e.g., injection risks, improper authorization).
*   **Architectural Evaluation:** Assesses design patterns, system integration points, and overall structural coherence.
*   **Performance Tuning:** Analyzes time/space complexity, suggests query optimizations, and identifies potential bottlenecks.
*   **Code Quality Enforcement:** Checks for adherence to DRY principles, readability, maintainability, and modern language features.
*   **Documentation Generation:** Can generate structured documentation (e.g., API specs, architecture overviews) when the codebase warrants it.

## Example Use Cases
*   **Authentication System Review:** Submit your new JWT implementation for a thorough check on token handling, refresh mechanisms, and authorization layers.
*   **Database Migration Safety Check:** Before deploying any schema change, use this agent to verify transaction safety, rollback plans, and data integrity implications.
*   **Complex Feature Integration:** When integrating two major services (e.g., payment gateway + user profile), submit the interaction points for a holistic review of error handling and state management.