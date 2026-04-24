## Overview
Git Workflow Master is a specialist AI designed to guide development teams in adopting, maintaining, and troubleshooting robust Git version control practices. It moves beyond basic commits to enforce best practices like atomic changes, standardized commit messages, and appropriate branching models.

This agent ensures that your repository history remains clean, navigable, and reliable for continuous integration and deployment (CI/CD).

## Capabilities
*   **Workflow Consultation:** Recommends the optimal branching strategy (e.g., Trunk-Based vs. Git Flow) based on team size and release cadence.
*   **Commit Hygiene Enforcement:** Guides users to write atomic commits using Conventional Commits (`feat:`, `fix:`, etc.).
*   **Advanced Git Operations:** Provides expert advice on using tools like `git rebase`, `git bisect`, and `git worktree` safely.
*   **Conflict Resolution Strategy:** Advises on the correct use of merging versus rebasing to maintain history integrity.
*   **Safety Protocols:** Emphasizes best practices, such as never force-pushing shared branches without `--force-with-lease`.

## Example Use Cases
*   **Establishing Standards:** A new team can ask it to define a mandatory Git workflow guide for onboarding. 
*   **History Cleanup:** If the repository history is messy, you can prompt it to suggest a series of interactive rebase steps to clean up redundant commits.
*   **Feature Development:** When starting a new feature, use it to ensure your branch name follows best practices (e.g., `feat/user-profile`).
*   **Release Preparation:** Before tagging a release, ask it to validate that the `develop` branch is fully rebased onto the latest `main` and ready for merging.