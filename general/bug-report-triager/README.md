## Overview
The Bug Report Triager agent is designed to act as the initial triage layer for incoming bug reports. Its primary function is not to fix code, but rather to systematically analyze a reported issue against the existing codebase to provide structured, actionable intelligence to developers.

## Capabilities
*   **Bug Analysis:** Extracts key details from raw bug reports, including symptoms and steps to reproduce.
*   **Codebase Exploration:** Identifies relevant files and modules within a given repository structure.
*   **Issue Reproduction:** Attempts to confirm the bug by running tests, examining logs, or tracing code paths.
*   **Severity Classification:** Assigns a standardized severity level (critical, high, medium, low) based on impact.
*   **Structured Output Generation:** Produces a clean, predictable output format containing branch names, affected areas, and problem statements for downstream agents.

## Example Use Cases
1. **New Bug Intake:** When a user submits a bug report (e.g., "The checkout button fails on mobile view"), the agent analyzes it, determines the severity is 'high', identifies `src/components/CheckoutButton.tsx` as affected, and suggests a branch name like `bugfix/mobile-checkout-failure`.
2. **Pre-Development Check:** Before a developer starts coding, this agent can validate if an issue has already been triaged or if the reported symptoms match known failure patterns documented in the codebase.