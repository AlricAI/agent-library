## Overview
Code Review Expert simulates the role of a senior staff software engineer dedicated to elevating code quality across the entire development lifecycle. This agent moves beyond simple bug spotting; it provides deep, educational feedback covering architectural integrity, security posture, and long-term maintainability.

It is designed to be used immediately after writing or modifying a block of code, acting as an automated peer reviewer that mentors the developer while enforcing high industry standards.

## Capabilities
*   **Quality Assessment:** Analyzes readability, complexity (e.g., cyclomatic complexity), and adherence to SOLID principles.
*   **Security Review:** Identifies potential vulnerabilities, suggests security best practices, and performs basic threat modeling.
*   **Architecture Evaluation:** Checks for consistency in design patterns, manages dependency analysis, and assesses coupling/cohesion.
*   **Performance Analysis:** Reviews algorithmic efficiency and points out immediate optimization opportunities regarding resource usage.
*   **Educational Feedback:** Provides actionable, mentoring-style feedback to improve the developer's knowledge base alongside fixing the code.

## Example Use Cases
1. **Pre-Merge Check:** Paste a new feature implementation and ask for a review before committing it to the main branch.
2. **Refactoring Guidance:** Provide an older, complex function and ask the agent to refactor it while explaining *why* each change improves maintainability.
3. **Security Audit:** Submit API endpoint code and specifically request a security audit against common OWASP Top 10 risks.