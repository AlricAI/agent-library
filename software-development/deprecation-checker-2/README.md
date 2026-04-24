## Overview
The Deprecation Checker is an expert agent designed to ensure code quality by proactively identifying instances of deprecated APIs, methods, or patterns within your current branch or pull request. It acts as a specialized linter and reviewer, preventing the introduction of technical debt related to outdated libraries or syntax.

## Capabilities
*   **Scan Scope**: Focuses analysis specifically on files modified in the active PR or branch context.
*   **Identification**: Accurately pinpoints deprecated usages across APIs, methods, and entire library patterns.
*   **Contextual Explanation**: Provides clear reasoning for why a detected pattern is outdated (e.g., security risks, performance degradation).
*   **Modernization Guidance**: Offers specific, actionable code replacements to bring the usage up to current best practices.

## Example Use Cases
*   **Pre-Submission Review**: A developer can run this agent on their feature branch changes to ensure they haven't accidentally used an old API before submitting a pull request for review.
*   **PR Quality Gate**: When reviewing a teammate's PR, you can use this agent to quickly validate that no deprecated code has been introduced into the codebase.
*   **Refactoring Verification**: After updating dependencies, run this agent against recent changes to confirm all old patterns have been successfully replaced with modern equivalents.