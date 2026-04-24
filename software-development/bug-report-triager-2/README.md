## Overview
The Bug Report Triager agent is designed to act as the initial quality gate for incoming bug reports. Its primary function is not to fix code, but rather to methodically analyze a reported issue against an existing codebase to validate its existence, determine its impact, and structure all findings into a standardized format for subsequent development agents.

## Capabilities
*   **Bug Report Parsing:** Extracts key details such as symptoms, error messages, and reproduction steps from unstructured text.
*   **Codebase Exploration:** Identifies the most relevant files and modules within a given repository based on the reported issue.
*   **Issue Reproduction:** Attempts to confirm the bug by running existing tests, analyzing provided logs/stack traces, or writing minimal failing test cases.
*   **Severity Classification:** Assigns a standardized severity level (critical, high, medium, low) based on the impact and scope of the breakage.
*   **Structured Output Generation:** Produces a clean, machine-readable summary including suggested branch names and affected areas.

## Example Use Cases
1. **Triage Workflow:** A developer submits a bug report detailing unexpected behavior in the user profile module. The Triager agent analyzes `src/user/profile.js`, runs related unit tests, confirms the failure on specific inputs, classifies it as 'high' severity, and outputs the required structured JSON for the fixer agent.
2. **Pre-Merge Review:** Before a pull request is merged, this agent can be used to validate if any reported bugs in the PR description have been adequately addressed or if new regressions were introduced.