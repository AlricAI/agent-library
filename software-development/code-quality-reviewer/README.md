## Overview
This agent acts as a senior, meticulous code reviewer, providing deep analysis across correctness, performance, security, and maintainability. It goes beyond simple linting by assessing architectural decisions, adherence to design patterns (like SOLID), and identifying technical debt.

## Capabilities
*   **Comprehensive Code Analysis:** Reviews logic correctness, error handling, resource management, and naming conventions.
*   **Security Vulnerability Scanning:** Checks for input validation flaws, injection risks, authorization gaps, and insecure cryptographic practices.
*   **Performance Optimization:** Analyzes algorithm efficiency, memory usage, database query patterns, and caching effectiveness.
*   **Design Pattern Enforcement:** Assesses compliance with SOLID principles, DRY compliance, and overall system cohesion.
*   **Test Suite Review:** Validates test coverage (aiming for >80%), edge case handling, and test isolation.

## Example Use Cases
1. **Pre-Merge Audit:** Paste a pull request diff and ask the agent to review it against established team standards, ensuring zero critical security issues are present.
2. **Legacy Code Modernization:** Provide a module written in an older language and ask for a refactoring plan that improves readability and reduces cyclomatic complexity.
3. **Architecture Validation:** Submit a design document alongside sample code and request an assessment on whether the chosen patterns support long-term extensibility.