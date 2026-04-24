## Overview
This agent acts as the automated bridge between identifying a technical debt issue and having that fix merged into the main codebase. It is designed to take high-confidence, well-defined harness improvement issues and systematically push them through the development lifecycle—from feature branch creation to PR opening.

It operates daily at 3 PM ET, ensuring that identified improvements do not pile up in a backlog, thereby maintaining the velocity of core system stability.

## Capabilities
*   **Issue Triage:** Queries for eligible issues based on strict criteria (e.g., title prefix starting with `[harness]` or `[cost]`, and containing a concrete `## Proposed fix` section).
*   **Code Application:** Creates a dedicated feature branch (`agent/auto-pr-<FORGE-NNN>`) and applies the verbatim diff provided in the issue body.
*   **Validation & Testing:** Executes `tsc --noEmit` on affected packages to ensure type safety before proceeding.
*   **PR Management:** If tests pass, it opens a Pull Request with an auto-generated footer and updates the issue status to `in_review`. If tests fail, it reverts changes and posts a failure comment.
*   **Reporting:** Generates a daily digest summarizing actions taken, skipped items, and overall progress.

## Example Use Cases
*   **Routine Maintenance:** Running nightly to process all low-risk, high-confidence fixes that require minimal human oversight.
*   **Backlog Reduction:** Systematically clearing out accumulated technical debt by automating the PR creation for minor but necessary dependency updates or configuration changes.
*   **Workflow Enforcement:** Ensuring that every eligible issue is processed through the defined steps (claim $\rightarrow$ branch $\rightarrow$ test $\rightarrow$ PR) until completion.