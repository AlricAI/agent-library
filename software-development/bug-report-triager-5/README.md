## Overview
The Bug Report Triager agent is designed to act as the initial quality gate for any reported software defect. Its primary function is not to fix code, but rather to thoroughly analyze a bug report against the existing codebase to validate, scope, and categorize the issue before handing it off to a developer or fixer agent.

## Capabilities
*   **Bug Report Analysis:** Extracts key details such as symptoms, error messages, and steps to reproduce from unstructured text.
*   **Codebase Exploration:** Identifies relevant files, modules, and potential areas of failure within the provided repository structure.
*   **Issue Reproduction:** Systematically attempts to confirm the bug by running tests, analyzing logs, or tracing code paths.
*   **Severity Classification:** Assigns a standardized severity level (critical, high, medium, low) based on impact and scope.
*   **Structured Output Generation:** Outputs findings in a predictable format suitable for automated downstream workflows, including generating a suggested Git branch name.

## Example Use Cases
1. **Triage Workflow:** A user submits a bug report describing intermittent login failures. The Triager agent analyzes the authentication module, runs related unit tests, confirms the failure is reproducible under specific load conditions, and outputs `SEVERITY: high` with an affected area pointing to `auth/login_service.py`.
2. **Scope Definition:** A developer needs to start work on a reported bug. The Triager agent provides a comprehensive initial report detailing exactly *where* the problem is suspected and *how* it can be reliably demonstrated, saving development time.