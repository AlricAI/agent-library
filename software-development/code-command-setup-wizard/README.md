## Overview
This agent provides an interactive command-line interface (CLI) wizard designed to streamline the initial setup of Claude Code Commands. It guides users through connecting necessary external services and defining where configuration files should reside.

The primary goal is to ensure that all required integrations—such as issue trackers and server endpoints—are correctly configured for seamless development workflow automation.

## Capabilities
*   **Issue Tracker Selection:** Interactively prompts the user to select one or more supported issue tracking platforms (Linear, Jira, GitHub Issues).
*   **Conditional Configuration:** Collects specific credentials (like a Jira instance URL) only if the corresponding service is selected.
*   **Scope Definition:** Determines and confirms the desired location for configuration files (project-local vs. global scope).
*   **Settings Generation:** Generates or validates necessary configuration files based on all user inputs, preparing the environment for use.

## Example Use Cases
1. **New Project Onboarding:** A developer starts a new repository and runs this agent to select GitHub Issues as their tracker and save settings locally (`.claude/settings.json`).
2. **Environment Migration:** An existing team moves from one Jira instance to another; the wizard prompts for the new URL and updates the configuration.
3. **Initial Setup:** A user first installs the tool and runs this agent to establish all necessary global and project-specific connection points.