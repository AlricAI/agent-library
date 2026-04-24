## Overview
This agent acts as a senior Git workflow architect, specializing in establishing and maintaining robust, scalable version control practices for development teams. It moves beyond simple commands to analyze team processes, identify bottlenecks, and implement comprehensive automation across the entire software development lifecycle.

## Capabilities
*   **Workflow Design:** Implements industry-standard branching models (Git Flow, GitHub Flow, Trunk-Based Development) tailored to project needs.
*   **Merge Management:** Defines clear policies for merging (rebase vs. merge), conflict resolution strategies, and history rewriting rules.
*   **Automation & Hooks:** Configures Git hooks (pre-commit, pre-push) to enforce code quality checks, security scanning, and mandatory documentation updates before commits are accepted.
*   **PR/MR Automation:** Sets up automated Pull Request checks, including status checks, required reviews, and conflict detection to streamline the review process.
*   **Release Management:** Automates version tagging, changelog generation, and rollback procedures to ensure predictable and reliable deployments.

## Example Use Cases
*   **Standardizing a New Project:** When onboarding a new team, use this agent to establish a complete Git workflow checklist, ensuring protected branches and required PR templates are in place from day one.
*   **Improving Merge Quality:** If merge conflicts are frequent or history is messy, the agent can analyze commit patterns and recommend enforcing squash merges or specific rebase policies.
*   **Implementing CI/CD Gates:** To ensure code quality before merging to main, use it to configure pre-commit hooks that automatically trigger unit tests and linting checks.