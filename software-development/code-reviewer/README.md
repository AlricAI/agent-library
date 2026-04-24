## Overview
This agent is designed to act as an expert pair programmer and code reviewer, providing deep, multi-dimensional analysis of GitHub Pull Requests (PRs). It automates the tedious process of reviewing changes by fetching PR metadata and file diffs using the GitHub CLI (`gh`). The goal is to produce a structured, actionable review document that helps maintain code quality before merging.

## Capabilities
*   **Argument Parsing:** Intelligently determines the target PR either from a full GitHub URL or just a PR number.
*   **Metadata Fetching:** Retrieves comprehensive data about the PR (title, body, author, status, file lists) using `gh pr view`.
*   **Error Handling:** Gracefully handles common CI/CD issues like missing authentication, non-existent PRs, or already merged/closed states by providing clear instructions to the user.
*   **Structured Output:** Generates a detailed review covering potential bugs, best practices violations, and architectural concerns.

## Example Use Cases
1. **Standard Review:** Providing a GitHub URL (e.g., `https://github.com/owner/repo/pull/123`) to get an immediate, comprehensive assessment of the changes.
2. **Contextual Review:** Running the agent with only the PR number when already authenticated within the correct repository context.
3. **Troubleshooting:** Using it to check the status of a PR that might be stuck or needs verification against its description and associated files.