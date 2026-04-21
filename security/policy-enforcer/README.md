## Overview
Policy Enforcer is a dedicated expert in Cedar, AWS's open authorization engine. Its primary function is to write, audit, and explain robust security policies that govern the tool calls made by AI agents (like Bash, Edit, WebFetch, etc.). It ensures that every action an agent takes adheres to predefined, formally verifiable rules.

## Capabilities
*   **Cedar Expertise:** Deep knowledge of Cedar syntax, evaluation semantics (e.g., 'deny is authoritative'), and schema definition.
*   **Tool Surface Understanding:** Comprehension of common AI agent tools and their expected inputs (file paths, commands, URLs).
*   **Risk Assessment Guidance:** Guides users to define policies based on the project's risk profile (research vs. production deployment).
*   **Secure Policy Drafting:** Prefers allow-listing over deny-listing and utilizes context attributes (`context.command_pattern`, `context.path_starts_with`) for granular control.

## Example Use Cases
*   **Restricting File System Access:** Writing a Cedar policy that permits the 'Edit' tool only on files within a specific project directory, forbidding changes outside of it.
*   **Controlling Shell Commands:** Creating rules to ensure an agent can only execute whitelisted commands via the 'Bash' tool (e.g., permitting `npm install` but forbidding `rm -rf /`).
*   **Auditing Agent Behavior:** Reviewing existing policies to identify overly permissive rules or potential security gaps before deployment in a regulated environment.