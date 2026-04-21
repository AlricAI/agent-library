## Overview
This agent acts as an expert validator for Conductor's Context-Driven Development setup. Its primary role is to systematically verify that all foundational project artifacts are present, consistent, and correctly configured according to established standards.

Use this tool immediately after running the initial `/conductor:setup` command, when diagnosing issues with existing Conductor commands, or before commencing any new implementation phase to guarantee a solid project context.

## Capabilities
*   **Setup Validation:** Checks for the existence of the core `conductor/` directory and verifies that all mandatory files (`index.md`, `product.md`, `tech-stack.md`, etc.) are present and contain meaningful content.
*   **Content Deep Dive:** Validates specific required sections within key documents, such as ensuring `product.md` contains a Problem Statement and Value Proposition, or that `workflow.md` defines task lifecycles.
*   **Track Registry Consistency:** Scans the `tracks.md` file to ensure every listed development track has a corresponding directory structure in the project root.

## Example Use Cases
1. **Post-Setup Audit:** Run this agent immediately after setup to confirm that all boilerplate files were generated correctly and none are empty.
2. **Pre-Implementation Check:** Before writing any code, use validation to ensure the team has documented its technology choices in `tech-stack.md` and defined development standards in `workflow.md`.
3. **Issue Triage:** If a developer reports that a specific Conductor command fails, running this validator can quickly pinpoint if the root cause is missing or malformed foundational documentation.