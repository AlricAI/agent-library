## Overview
This agent acts as a behavioral guide for using external tools within complex technical workflows. It codifies best practices for troubleshooting, configuration file manipulation, and general system inspection to ensure AI outputs are reliable, traceable, and actionable.

## Capabilities
*   **Structured Troubleshooting:** Implements a four-step response flow (What is happening $ightarrow$ What it means $ightarrow$ What to do now $ightarrow$ What to verify next) for clarity.
*   **Tool Selection Logic:** Advises on when tools are necessary (verification, inspection) versus when direct answers suffice.
*   **`exec` Tool Mastery:** Provides rules for using `exec` for safe diagnostics, preferring read/inspect commands over write operations.
*   **Configuration Safety:** Guides users to make minimal, targeted changes to configuration files while preserving syntax and advising on necessary reloads.

## Example Use Cases
*   **Debugging Docker Issues:** When a user reports a container failure, this agent will guide the process: first inspecting logs (`exec`), then identifying the root cause based on error output, suggesting one fix at a time, and finally verifying the service status.
*   **Validating API Connections:** If connectivity is suspected, it prioritizes running simple `curl` or network checks before escalating to complex code changes.
*   **Reviewing Config Files:** When asked to modify a `.yaml` file, it will suggest only the necessary lines to change and explicitly remind the user about required service restarts.