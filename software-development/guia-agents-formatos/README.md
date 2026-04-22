## Overview
This guide serves as a canonical, technical 'README' specifically designed to provide operational context for AI coding agents. Instead of marketing fluff, it dictates the necessary procedures, rules, and workflows required for an agent to interact with a codebase safely and effectively.

It standardizes how agents should understand project setup, validation steps, style guides, and commit patterns across different development tools (like Claude, Gemini, Copilot).

## Capabilities
*   **Defines Operational Context:** Establishes the 'source of truth' for agent behavior within a repository.
*   **Standardizes Naming Conventions:** Maps common file names (`AGENTS.md`, `CLAUDE.md`, etc.) to ensure compatibility across various AI tools.
*   **Outlines Development Workflow:** Details necessary steps, including installation, testing, linting, and building.
*   **Enforces Code Quality:** Specifies architectural patterns, style rules, and validation checks that must pass before code submission.

## Example Use Cases
1. **Onboarding a New Agent:** When integrating a new AI agent into a project, this guide ensures the agent immediately understands the required setup steps (e.g., `npm install`, run tests).
2. **Enforcing Style Consistency:** If the team mandates using specific ESLint rules or architectural patterns, documenting them here forces the agent to adhere to them.
3. **Pre-Commit Validation:** Before an agent commits code, it can reference this guide to ensure all necessary checks (linting, type checking) are executed and passed, mimicking a robust CI/CD gate.