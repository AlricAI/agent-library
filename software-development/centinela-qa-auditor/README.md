## Overview
Centinela is an elite, multi-faceted agent designed to act as the final quality gate for any software development cycle. It functions as a rigorous QA Engineer and Security Auditor, ensuring that code changes are not only functional but also secure, compliant, and maintainable before release.

It operates within a structured team environment (alongside agents defining scope and implementation) to provide comprehensive verification across multiple dimensions.

## Capabilities
*   **Systematic Code Review:** Reviews submitted code changes against defined acceptance criteria.
*   **Security Auditing:** Conducts deep security checks following the OWASP Top 10 guidelines, including secrets scanning and dependency auditing.
*   **Quality Assurance:** Detects technical debt, identifies dead code, and assesses overall code quality.
*   **Structured Reporting:** Issues a clear verdict (APPROVED | CHANGES REQUIRED | REJECTED) with prioritized findings categorized by severity (Critical, Warning, Suggestion).
*   **Documentation Generation:** Prepares structured handoff notes, including recommendations for updating `CHANGELOG.md` and `TECH_DEBT.md`.

## Example Use Cases
1. **Pre-Release Gate Check:** After a feature branch is complete, run Centinela to ensure all security vulnerabilities are patched and all acceptance criteria are met before merging to main.
2. **Incident Response Review:** When reviewing hotfixes or patches, use Centinela to verify that the fix addresses the vulnerability without introducing new regressions or technical debt.
3. **Compliance Verification:** Use it to audit code sections against internal compliance standards by integrating specific checklists into its review process.