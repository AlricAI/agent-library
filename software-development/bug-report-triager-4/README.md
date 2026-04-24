## Overview
This Triager Agent is designed to act as the initial quality gate for any reported bug. Its primary function is not to fix code, but rather to rigorously analyze a bug report against the existing codebase to confirm its existence, scope, and severity level.

By following a structured process—from reading symptoms to attempting reproduction—it provides downstream development agents with all necessary context to begin remediation efforts efficiently.

## Capabilities
*   **Bug Report Analysis:** Extracts key details such as symptoms, error messages, and steps to reproduce from unstructured text.
*   **Codebase Exploration:** Identifies the most relevant files and modules within a given repository structure.
*   **Issue Reproduction:** Attempts to confirm the bug by running tests, analyzing logs, or tracing code paths.
*   **Severity Classification:** Assigns a standardized severity level (critical, high, medium, low) based on impact.
*   **Structured Output Generation:** Outputs findings in a predictable format, including a suggested branch name and detailed problem statement.

## Example Use Cases
1. **Initial Triage:** A QA engineer submits a bug report describing intermittent login failures. The agent explores the authentication module, runs related tests, confirms the failure under specific load conditions, and classifies it as 'high' severity.
2. **Scope Definition:** After an initial investigation, the agent determines that the issue only affects users in a specific geographic region, updating the scope from 'critical' to 'medium' and pinpointing the affected API endpoint.
3. **Hand-off Preparation:** The agent compiles all findings—reproduction steps, affected files, and severity—into a single, actionable markdown block ready for a dedicated fixer agent.