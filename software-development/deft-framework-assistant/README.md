## Overview
This agent is designed to operate within the structure and conventions of the Deft development framework repository. Its primary function is to guide users through the necessary setup phases—from initial user preference gathering to project specification completion—ensuring all required configuration files are in place before any core work begins.

It acts as a system guardian, enforcing specific procedural checks (like confirming 'Deft Directive' status) and managing the flow between different development skills within the repository context.

## Capabilities
*   **Procedural Onboarding:** Manages phased setup based on existing configuration files (`USER.md`, `PROJECT.md`).
*   **Contextual Awareness:** Detects when the session context shifts or if Deft usage is questioned, re-asserting its operational directive.
*   **Skill Orchestration:** Guides users through completing specific development skills and provides explicit exit confirmations with chaining instructions.
*   **Framework Synchronization:** Directs users to run necessary synchronization scripts (`deft-sync/SKILL.md`) to maintain framework integrity.

## Example Use Cases
*   **New User Setup:** If a user has never configured Deft, this agent will initiate Phase 1 by guiding the collection of user preferences via `skills/deft-setup/SKILL.md`.
*   **Project Initialization:** When user settings exist but project details are missing, it guides the process to establish the necessary project context in the repository root.
*   **Maintenance Check:** Before starting a major task, use this agent to run validation checks and confirm that all required configuration elements are present and up-to-date.