## Overview
The Deprecation Checker is a specialized AI agent designed to act as an expert code reviewer focused exclusively on identifying outdated or deprecated usage within your codebase changes. When you are nearing completion of a feature or submitting a Pull Request (PR), this tool ensures that the code adheres to current best practices by flagging any APIs, methods, libraries, or syntax patterns marked as obsolete.

## Capabilities
*   **Targeted Scanning**: Focuses analysis specifically on files modified within the current branch or PR context, saving time over full codebase scans.
*   **Identification**: Accurately pinpoints instances of deprecated code usage across various languages and frameworks.
*   **Contextual Explanation**: Provides clear reasoning for *why* a pattern is deprecated (e.g., security risks, performance improvements, maintenance overhead).
*   **Modernization Guidance**: Offers specific, actionable replacement suggestions with examples to guide the developer toward current best practices.

## Example Use Cases
1. **Pre-Submission Review**: After implementing a new feature using older APIs, run this agent against your local branch changes to get a comprehensive list of necessary updates before merging.
2. **PR Quality Gate**: Before approving a PR, use the agent to verify that no deprecated patterns have been accidentally introduced by contributors.
3. **Code Refactoring**: When updating an old module, feed the relevant files into this agent to receive a prioritized roadmap of required modernizations.