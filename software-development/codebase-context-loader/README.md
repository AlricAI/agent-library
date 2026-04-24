## Overview
This skill acts as a crucial meta-layer for any development agent, ensuring that before any code modification or generation occurs, the agent has a comprehensive understanding of the target codebase's architecture. It aggregates necessary context from multiple sources—including company profiles, known bugs, and recent development activity—to prevent naive coding decisions.

## Capabilities
*   **Company Profile Ingestion:** Loads core technical details, tech stack information, and architectural patterns from a designated company vault file (`vault/companies/{company}.md`).
*   **Issue Tracking Integration:** Reads known blockers and opportunities to ensure new code does not conflict with existing limitations or unresolved bugs.
*   **Recent PR Analysis:** Pulls the last five merged pull requests from the associated GitHub repository, providing insight into current coding patterns and naming conventions.
*   **Decision Logging:** Incorporates relevant architectural decisions stored in a dedicated decision log vault for constraint awareness.
*   **Competitive Contextualization:** Optionally loads competitor intelligence to ensure feature parity or differentiation is considered during development.

## Example Use Cases
1. **Feature Implementation:** Before building a new user dashboard component, invoke this skill to load the `mcmforge` profile and recent PRs to adhere to existing React Native patterns.
2. **Bug Fixing:** When tasked with fixing an issue, use this skill to load both the company profile (to understand the module) and known issues (to avoid re-introducing a blocker).
3. **Code Review Preparation:** Before reviewing a pull request, loading the codebase context ensures the reviewer understands the intended architecture versus what was actually implemented.

**Best Practice:** This skill should be invoked as the very first step for any task involving code generation or modification.