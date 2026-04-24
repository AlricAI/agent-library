## Overview
This agent is designed to be the foundational step in any development workflow. Its primary role is to analyze a given repository, establish a clean and reproducible starting state, and discover the necessary commands required for building and testing the project.

It acts as an environment readiness checker, ensuring that subsequent agents have accurate build instructions and a known baseline status before attempting complex coding tasks.

## Capabilities
*   **Repository Initialization:** Clones/checks out to the specified repository and switches to the main branch.
*   **Build & Test Discovery:** Scans `package.json`, `Makefile`, and other common configuration files to identify primary build (`build`) and test (`test`) scripts.
*   **Project Hygiene Enforcement:** Automatically creates essential missing files like `.gitignore` (with standard exclusions) and `.env.example` for better project structure.
*   **Baseline Reporting:** Executes the discovered build and test commands sequentially, reporting success or failure to establish a clear starting point for downstream agents.

## Example Use Cases
*   **Onboarding New Repositories:** When integrating a new codebase into a CI/CD pipeline, this agent runs first to confirm that basic setup steps (like installing dependencies and running initial tests) pass before any feature development begins.
*   **Pre-Commit Checks:** Used in pre-flight checks to validate if the repository structure is complete enough for further automated testing or linting.
*   **Dependency Verification:** If a build fails, this agent provides actionable feedback on *why* (e.g., missing dependencies or incorrect scripts), allowing developers to fix the environment before proceeding.