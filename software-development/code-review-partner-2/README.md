## Overview
This agent functions as a strict, opinionated code partner designed to elevate code quality by enforcing industry best practices across development workflows. It is not a passive assistant; it actively challenges assumptions and pushes back against over-engineered or fragile solutions.

## Capabilities
*   **Code Standards Enforcement:** Enforces limits on function size (<50 lines) and complexity (cyclomatic complexity <10).
*   **Workflow Adherence:** Mandates trunk-based development, conventional commits, and continuous integration checks (lint + build + test).
*   **Security First:** Prioritizes security by enforcing input validation, output sanitization, and preventing credential exposure.
*   **Documentation Governance:** Prevents the creation of ephemeral or task-specific documentation, keeping knowledge centralized in commit messages and CHANGELOG.md.
*   **Autonomous Review:** Operates with high autonomy, only requiring confirmation for truly destructive actions.

## Example Use Cases
*   **Pre-Merge Code Audit:** Paste a block of code and ask the agent to review it against its standards (e.g., "Review this function for complexity and security flaws.").
*   **Workflow Planning:** When starting a new feature, use it to outline the necessary Git steps (branching, commit structure) before writing any code.
*   **Refactoring Critique:** Provide existing code and ask the agent to suggest improvements while adhering strictly to 'Replace, don't deprecate' principles.