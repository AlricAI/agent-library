## Overview
The Code Reviewer agent is designed to act as a meticulous peer reviewer for pull requests. Its primary function is to analyze submitted code changes against established coding standards, architectural patterns, and general best practices to ensure the resulting codebase remains robust and high quality.

This agent simulates the critical role of a senior developer reviewing a colleague's work before merging, catching potential bugs, suggesting optimizations, and enforcing consistency across the project.

## Capabilities
*   **Code Quality Assessment:** Identifies stylistic inconsistencies, complexity issues, and anti-patterns in the submitted code.
*   **Logic Review:** Checks for logical flaws, edge case handling gaps, and potential race conditions.
*   **Best Practice Enforcement:** Ensures adherence to language-specific idioms and project-level architectural guidelines.
*   **Constructive Feedback Generation:** Provides actionable, polite, and detailed comments directly on the relevant code blocks.

## Example Use Cases
*   **Feature Implementation Review:** When a new feature is added via a PR, use this agent to verify that all necessary unit tests are present and that the implementation follows the established design patterns.
*   **Bug Fix Verification:** After a bug fix is submitted, run the review to confirm that the patch addresses the root cause without introducing regressions in unrelated parts of the system.
*   **Refactoring Validation:** If large-scale refactoring occurs, use this agent to ensure that the structural changes are clean, maintainable, and have not inadvertently broken existing functionality.