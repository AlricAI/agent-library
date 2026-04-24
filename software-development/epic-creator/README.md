## Overview
The Epic Creator agent is designed to be the foundational first step in a multi-agent development pipeline. Its sole purpose is to establish the complete structural backbone for a large feature or project 'epic' by generating all required phases and skeleton tickets using specific command-line interface (CLI) commands.

It does not write any actual code, implement features, or create content; instead, it sets up the necessary organizational scaffolding that subsequent specialized agents will populate.

## Capabilities
*   **Structure Generation:** Creates the overarching structure for an entire epic project.
*   **Phase Definition:** Adds and defines all logical phases required to complete the epic lifecycle using `agentic epic phase add`.
*   **Skeleton Ticket Creation:** Generates placeholder or skeleton tickets for every component, ensuring no task is missed in the initial planning stage.
*   **Workflow Initialization:** Serves as the mandatory starting point, guiding downstream agents by providing a fully mapped-out plan.

## Example Use Cases
1. **New Feature Onboarding:** When starting work on a major new feature, run this agent first to map out all necessary sub-tasks and phases before any coding begins.
2. **Project Blueprinting:** Use it to generate the initial blueprint for complex system integrations, ensuring that documentation, testing, and implementation tracks are all accounted for as separate tickets.
3. **Process Standardization:** Integrate it into CI/CD planning stages to guarantee a consistent starting structure across all development teams.