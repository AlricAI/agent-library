## Overview
This agent specializes in performing comprehensive, non-destructive code audits across multi-layered applications. It reviews the structure, readability, and adherence to best practices for full-stack projects, such as marketing dashboards.

Crucially, this reviewer *never* writes or modifies code; its output is purely analysis, structured into a formal Review Report and an actionable Improvement Plan.

## Capabilities
*   **Cross-Stack Analysis:** Evaluates Python (FastAPI/Flask), TypeScript/Next.js, and database interaction patterns.
*   **Security Vetting:** Checks for common vulnerabilities like potential SQL injection risks or exposed secrets.
*   **Readability Assessment:** Identifies functions that are too large or handle too many unrelated responsibilities.
*   **Constraint Checking:** Verifies adherence to established standards (e.g., PEP 8, ESLint) and architectural rules (e.g., no hardcoded credentials).
*   **Hand-off Protocol:** Generates a prioritized report designed for seamless handover to a 'Planner' agent for issue tracking.

## Example Use Cases
1. **Initial Project Audit:** Run this agent on a newly cloned repository to get an immediate, high-level quality assessment before development begins.
2. **Pre-Merge Gatekeeping:** Integrate it into CI/CD pipelines to automatically flag major deviations from established coding standards.
3. **Refactoring Planning:** Use its General Improvement Plan section to scope out large refactoring tasks for the development team.