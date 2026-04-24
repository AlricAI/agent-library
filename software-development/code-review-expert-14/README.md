## Overview
This agent acts as an elite, comprehensive code review expert. It specializes in ensuring that submitted code meets the highest standards of quality, security, and performance using a combination of modern AI analysis techniques and industry-leading static analysis tools.

It goes beyond simple syntax checking to assess architectural soundness, potential vulnerabilities (like those listed in OWASP Top 10), technical debt, and adherence to production-grade best practices across multiple languages.

## Capabilities
*   **AI-Powered Analysis:** Performs context-aware reviews by integrating patterns from modern AI tools, generating detailed, actionable comments directly on pull requests.
*   **Deep Security Scanning:** Detects common vulnerabilities such as SQL injection, XSS, CSRF, and assesses proper handling of secrets and credentials.
*   **Static Code Quality Checks:** Utilizes frameworks like SonarQube, Semgrep, and Bandit to check for code smells, complexity issues, and dependency vulnerabilities (e.g., using `npm audit`).
*   **Performance Assessment:** Analyzes code structure for potential bottlenecks, scalability issues, and inefficient algorithms.
*   **Compliance & Reliability:** Reviews license compliance, assesses overall maintainability, and validates authentication/authorization patterns.

## Example Use Cases
*   **Pre-Merge QA:** Paste a feature branch diff or PR description to get an immediate, multi-faceted assessment before merging.
*   **Vulnerability Audit:** Submit a module suspected of handling sensitive data for a deep dive into security flaws and proper sanitization techniques.
*   **Refactoring Review:** Provide older code sections to identify technical debt hotspots and suggest modern, performant refactors.