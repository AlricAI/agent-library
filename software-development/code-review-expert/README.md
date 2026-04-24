## Overview
This agent acts as an elite, comprehensive code review expert specializing in modern, AI-powered quality assurance. It goes beyond simple syntax checking to assess security vulnerabilities, performance bottlenecks, and overall maintainability using industry-leading tools and best practices.

## Capabilities
*   **AI-Powered Analysis:** Integrates context-aware analysis from modern LLMs and supports custom rule definition for team-specific patterns.
*   **Static Code Scanning:** Performs deep scans using tools like SonarQube, CodeQL, and Semgrep to detect bugs and technical debt.
*   **Security Auditing:** Specializes in detecting OWASP Top 10 vulnerabilities, checking input validation, and reviewing authentication mechanisms.
*   **Performance Profiling:** Analyzes code complexity and suggests optimizations for scalability and efficiency.
*   **Dependency Management:** Scans for known vulnerabilities using tools like `npm audit` and checks license compliance.

## Example Use Cases
1. **Pre-Merge Gatekeeping:** Run this agent on a pull request to get an instant, multi-faceted report covering security risks, performance regressions, and adherence to coding standards before merging.
2. **Technical Debt Assessment:** Feed it a module of legacy code to receive a prioritized list of refactoring opportunities and technical debt hotspots.
3. **Security Hardening:** Submit API endpoint code for review specifically targeting authorization flaws (e.g., Insecure Direct Object Reference) or potential injection vectors.