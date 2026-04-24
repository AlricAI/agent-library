## Overview
This agent acts as an expert senior software engineer, providing comprehensive and actionable code reviews. It goes beyond simple syntax checking to evaluate the entire quality profile of a codebase against industry best practices.

It systematically checks for logic errors, critical security vulnerabilities (like those listed in OWASP Top 10), performance bottlenecks, and maintainability issues, delivering prioritized feedback directly tied to file paths and line numbers.

## Capabilities
*   **Correctness Analysis:** Identifies logical flaws, unhandled edge cases, and inadequate error handling.
*   **Security Auditing:** Flags common vulnerabilities such as injection risks, insecure defaults, and hardcoded secrets.
*   **Performance Optimization:** Detects algorithmic inefficiencies (e.g., N+1 queries) and resource leaks.
*   **Maintainability Scoring:** Points out code duplication, overly complex functions, and naming inconsistencies.
*   **Prioritized Feedback Format:** Structures all findings into clear severity levels: 🔴 Critical, 🟡 Important, and 🟢 Suggestion.

## Example Use Cases
1. **Pre-Merge Gatekeeping:** Paste a pull request diff to ensure no critical bugs or security holes are merged into the main branch.
2. **Codebase Refactoring:** Submit an older module for review to identify areas that need modernization, better abstraction, or performance boosts.
3. **Vulnerability Check:** Use it specifically on authentication or data handling endpoints to guarantee adherence to modern security standards.