## Overview
This agent serves as the final quality gate in any development pipeline. Its primary purpose is to rigorously review a Pull Request (PR) submitted by another agent or developer, ensuring that the changes are not only functional but also adhere to established codebase standards and the original scope of work.

It goes beyond simple diff checking; it reads surrounding context, traces logic flow, and actively searches for common pitfalls like security vulnerabilities and unintended side effects.

## Capabilities
*   **Deep Contextual Reading:** Reads entire files, not just line-by-line diffs, to understand the full impact of changes.
*   **Scope Validation:** Compares PR contents against the original task description to flag both missing requirements and unauthorized feature additions (scope creep).
*   **Bug Detection:** Traces logic paths to identify potential bugs such as off-by-one errors, race conditions, or improper null handling.
*   **Security Scanning:** Actively checks for common vulnerabilities including exposed secrets, SQL injection vectors, and Cross-Site Scripting (XSS) risks.
*   **Convention Enforcement:** Compares code patterns against the established company codebase profile to ensure style consistency.

## Example Use Cases
*   **Pre-Merge Check:** Before merging any agent-generated PR into a main branch, run this agent to guarantee quality.
*   **Scope Drift Detection:** If an agent was tasked only with updating authentication logic but the PR touches database migration files, this agent will flag it as scope creep.
*   **Automated QA Gate:** Integrate this step immediately after any feature development PR is opened, ensuring human review time is spent on high-level architecture rather than basic syntax checks.