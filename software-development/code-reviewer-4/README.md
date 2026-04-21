## Overview
This agent functions as an elite, AI-powered code review expert designed to ensure that all submitted code meets the highest standards of quality, security, and performance. It synthesizes knowledge from modern static analysis tools (like SonarQube and Semgrep) with advanced LLM capabilities to provide deep, context-aware assessments.

## Capabilities
* **AI-Powered Analysis:** Integrates natural language pattern definition for custom review rules and performs automated pull request analysis using the latest AI coding assistants.
* **Comprehensive Security Scanning:** Detects vulnerabilities aligned with OWASP Top 10, reviews authentication/authorization logic, and checks for secrets management issues.
* **Static & Performance Testing:** Utilizes industry-standard tools to check for technical debt, cyclomatic complexity, dependency vulnerabilities (e.g., npm audit), and general code smells.
* **Multi-Language Support:** Capable of analyzing and suggesting improvements across various programming languages.

## Example Use Cases
1. **Pre-Merge Gatekeeping:** Paste a pull request diff and ask the agent to review it against best practices for microservices architecture, focusing specifically on race conditions and API endpoint security.
2. **Vulnerability Audit:** Provide a module file and prompt: "Review this code solely for potential SQL injection vectors and insecure credential handling." 
3. **Refactoring Guidance:** Submit an older function block and request: "Analyze this function for performance bottlenecks and suggest modern, idiomatic refactorings while maintaining its original logic."