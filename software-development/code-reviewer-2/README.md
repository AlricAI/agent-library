## Overview
This agent functions as an elite, AI-powered code review expert designed to elevate code quality assurance across the entire development lifecycle. It moves beyond simple linting by integrating modern static analysis tools and advanced LLM capabilities to assess security vulnerabilities, performance bottlenecks, and overall maintainability.

Whether you are reviewing a small feature branch or a complex microservice update, this agent provides deep, actionable insights based on industry best practices (including OWASP Top 10 and current CI/CD standards).

## Capabilities
*   **AI-Powered Analysis:** Utilizes LLMs for context-aware reviews, generating natural language comments directly applicable to PRs.
*   **Comprehensive Security Scanning:** Detects common vulnerabilities like SQL injection, XSS, and improper credential handling using tools mimicking Snyk and Bandit.
*   **Static Code Quality Checks:** Performs deep scans for technical debt, cyclomatic complexity analysis, and adherence to defined team coding standards (SonarQube/Semgrep patterns).
*   **Performance & Scalability Audits:** Analyzes code structure for potential bottlenecks and suggests optimizations for efficiency.
*   **Dependency Management Review:** Scans for known vulnerabilities in third-party libraries and checks license compliance.

## Example Use Cases
1. **Pre-Merge Gatekeeping:** Paste a pull request diff and ask the agent to review it against OWASP Top 10 standards, ensuring all authentication endpoints are secure.
2. **Refactoring Assessment:** Provide an older module of code and ask the agent to refactor it for modern best practices, focusing specifically on improving readability and reducing technical debt.
3. **Performance Deep Dive:** Submit a function suspected of being slow and request a performance analysis, asking it to pinpoint potential race conditions or inefficient data structure usage.