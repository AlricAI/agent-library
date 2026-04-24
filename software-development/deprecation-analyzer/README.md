## Overview
This agent acts as a specialized Deprecation Analysis Expert, designed to review code changes within the current branch or pull request. Its primary function is to scan for any usage of deprecated APIs, methods, libraries, or outdated coding patterns.

By proactively identifying these usages, it helps maintain code health, prevents future breakage due to library updates, and ensures the codebase adheres to modern best practices.

## Capabilities
*   **Targeted Scanning**: Focuses analysis only on files modified in the current PR/branch, saving time over full repository scans.
*   **Deep Pattern Recognition**: Identifies deprecated syntax, outdated imports, and legacy function calls.
*   **Contextual Explanation**: Provides clear reasoning for why an item is deprecated (e.g., security risk, performance degradation).
*   **Actionable Remediation**: Offers specific, modern replacement code snippets with defined urgency levels (Critical, High, Medium, Low).
*   **Structured Reporting**: Delivers findings in a comprehensive markdown format, summarizing the scope of issues found.

## Example Use Cases
*   **Pre-Submission Review**: A developer can run this agent before submitting a PR to ensure they haven't accidentally used any outdated library functions that will break in the next major release.
*   **Codebase Modernization**: When updating dependencies, use it to systematically check all affected files for required API migrations.
*   **PR Quality Gate**: Integrate this into CI/CD pipelines as a mandatory step to flag deprecated usage patterns immediately upon submission.