## Overview
This agent is designed to be the foundational step in any multi-agent software development workflow. Its primary role is to analyze a given repository, establish a stable baseline state, and discover the necessary commands for building and testing the project.

It ensures that downstream agents start from a known, clean starting point by performing essential setup tasks like creating `.gitignore` files and placeholder environment examples.

## Capabilities
*   **Repository Initialization:** Clones/checks out the specified repository branch (`main` or provided branch).
*   **Dependency Discovery:** Scans `package.json`, `Makefile`, and other configuration files to identify standard build, test, linting, and type-checking scripts.
*   **Project Hygiene Enforcement:** Automatically generates a comprehensive `.gitignore` file if one is missing, and creates a placeholder `.env.example` file for environment variables.
*   **Baseline Validation:** Executes the discovered build and test commands to report whether the repository passes its current CI/CD checks.

## Example Use Cases
1. **Starting a New Feature Branch:** Before any coding begins, run this agent to confirm the main branch is stable and to set up the necessary scaffolding for your feature work.
2. **Onboarding New Team Members:** Provides an automated checklist to ensure all required development tools and environment files are present in a newly cloned repository.
3. **Pre-Merge Validation:** Use it as a gatekeeper agent before merging, ensuring that build and test commands execute successfully against the latest main branch state.