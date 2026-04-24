## Overview
This meta-skill is designed to be the foundational step for any agent tasked with modifying or analyzing a codebase. It ensures that before writing a single line of code, the AI agent has ingested the full architectural context, preventing common pitfalls like inconsistent patterns, incorrect database schema assumptions, or overlooking necessary test setups.

## Capabilities
*   **Full Context Loading:** Ingests the company profile detailing the primary framework and technology stack.
*   **Issue Awareness:** Loads known issues and blockers documented within the company profile for immediate consideration.
*   **Pattern Recognition:** Analyzes the five most recently merged Pull Requests to adopt established coding patterns and naming conventions.
*   **Decision Logging:** Incorporates relevant decision logs from the vault/decisions directory, ensuring adherence to past architectural choices.

## Example Use Cases
*   **Bug Fixing:** When performing a visual bug fix, this skill ensures the agent understands surrounding modules and dependencies before patching the issue.
*   **Feature Implementation:** Before executing a 'plan-then-code' sequence for a new feature, running this skill guarantees the plan respects existing architectural boundaries.
*   **Code Review:** It provides reviewers with the necessary background context—including recent PR patterns—to give highly accurate and actionable feedback.