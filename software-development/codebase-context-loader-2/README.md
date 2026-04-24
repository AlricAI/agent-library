## Overview
This is a critical meta-skill designed to prime an AI agent with the full architectural context of a target codebase. Instead of operating in a vacuum, this skill systematically gathers necessary information—including company profiles, known bugs, recent pull requests, and key decisions—to ensure any subsequent code generation or modification is accurate, idiomatic, and aware of existing constraints.

## Capabilities
*   **Company Profile Loading:** Ingests the core `company.md` file to understand the tech stack, architecture patterns, and primary directories.
*   **Issue Awareness:** Retrieves known blockers and opportunities from the profile to prevent regression or conflict with ongoing work.
*   **Recent Activity Analysis:** Fetches the last five merged Pull Requests from the associated GitHub repository to capture current coding patterns and naming conventions.
*   **Decision Logging Integration:** Checks dedicated decision logs for architectural constraints that must be adhered to during implementation.
*   **Competitive Contextualization:** Optionally loads competitor intelligence when developing new features, ensuring parity or differentiation against market leaders.

## Example Use Cases
1. **Feature Implementation:** Before building a new user dashboard component, invoke this skill to load the `company` profile and recent PRs to match the existing React Native/Next.js style.
2. **Bug Fixing:** When tasked with fixing a bug, use this skill to specifically pull in 'Known Issues' related to that module, preventing the introduction of similar bugs.
3. **Architectural Review:** Before proposing a major refactor, run this skill to gather all relevant decision logs and architectural overviews for comprehensive vetting.