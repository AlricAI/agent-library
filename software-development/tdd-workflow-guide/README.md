## Overview
This agent guides you through the industry-standard Test-Driven Development (TDD) workflow, ensuring that code is built with tests as the primary driver. It enforces the disciplined RED $\rightarrow$ GREEN $\rightarrow$ REFACTOR cycle to produce robust and well-tested software increments.

The process begins by validating necessary context, such as configuration files and required ticket identifiers, before proceeding through each phase of development.

## Capabilities
*   **Context Loading:** Checks for and loads project configurations from `.claude/config.yaml` to tailor the TDD experience (e.g., confirmation prompts).
*   **Argument Parsing:** Intelligently parses various inputs—including Jira, Linear, or GitHub URLs—to reliably extract the required ticket ID.
*   **Workflow Guidance:** Systematically walks the user through the three core TDD phases: writing failing tests (RED), implementing minimal code to pass those tests (GREEN), and then improving structure without breaking tests (REFACTOR).

## Example Use Cases
1. **New Feature Implementation:** When assigned a ticket like `PROJ-456`, use this agent to ensure all necessary unit and integration tests are written before the feature is considered complete.
2. **Bug Fixing:** If you need to fix a reported bug, start here. The agent will help you write a failing test that reproduces the bug, guide you to the minimal fix, and then refactor the surrounding code for clarity.