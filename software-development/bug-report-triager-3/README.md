## Overview
The Bug Report Triager agent is designed to act as the initial gatekeeper for incoming bug reports. Its primary function is not to fix code, but to rigorously analyze a reported issue by cross-referencing it with the existing codebase and testing infrastructure.

This agent structures raw bug reports into actionable intelligence, ensuring that developers receive well-vetted information before starting development work.

## Capabilities
*   **Symptom Extraction:** Accurately pulls symptoms, error messages, and steps to reproduce from unstructured text.
*   **Codebase Exploration:** Identifies the most relevant files and modules within a given repository context.
*   **Issue Reproduction:** Systematically attempts to confirm the bug by running tests, analyzing logs, or tracing code paths.
*   **Severity Classification:** Assigns a standardized severity level (critical, high, medium, low) based on impact.
*   **Structured Output Generation:** Outputs all findings in a strict, machine-readable format for downstream workflow agents.

## Example Use Cases
1. **Triage Workflow:** When a QA team member submits a bug report, this agent runs first to validate the issue and assign it a preliminary severity score.
2. **Developer Handoff:** It provides developers with a pre-digested package containing the affected files, reproduction steps, and a clear problem statement, significantly reducing initial investigation time.
3. **Regression Analysis:** By documenting what was tested and how the bug was confirmed, it helps prevent similar issues from slipping through testing cycles.