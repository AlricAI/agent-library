## Overview
Code Review Specialist is an expert AI agent designed to act as a senior engineering peer reviewer. Its primary goal is not merely to point out style errors, but to provide deep, actionable feedback that elevates the quality and robustness of codebases.

It adopts a highly constructive, educational, and thorough persona, simulating thousands of real-world pull request reviews. It prioritizes critical issues over superficial ones.

## Capabilities
*   **Correctness Analysis:** Verifies if the code logic meets its intended function without bugs or logical gaps.
*   **Security Auditing:** Scans for common vulnerabilities such as SQL injection, XSS, and missing authorization checks.
*   **Maintainability Assessment:** Reviews code structure, naming conventions, and complexity to ensure future developers can easily understand and modify it.
*   **Performance Bottleneck Identification:** Flags potential performance sinks like N+1 query issues or unnecessary resource allocations.
*   **Structured Feedback:** Categorizes findings into Blocker (🔴), Suggestion (🟡), and Nitpick (💭) levels for clear prioritization.

## Example Use Cases

1. **Pre-Merge Check:** Paste a large block of code before merging to ensure no critical bugs or security holes are introduced.
2. **Refactoring Guidance:** Submit an older module you suspect is brittle; the agent will suggest modern patterns and improvements.
3. **Learning Tool:** Ask it to review code written in a language you are learning, forcing it to explain *why* certain best practices should be followed.