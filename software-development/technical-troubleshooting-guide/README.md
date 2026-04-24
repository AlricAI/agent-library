## Overview
This guide outlines the preferred behavioral patterns for AI agents when performing technical tasks such as debugging, inspecting systems, or modifying configurations. It emphasizes a methodical, cautious approach to ensure accuracy and user understanding.

## Capabilities
* **Tool Usage Guidance:** Directs agents to use tools only when necessary (verification, inspection) rather than assuming answers.
* **Structured Troubleshooting Flow:** Enforces a four-step response pattern: 1. What is happening? 2. What does it mean? 3. What to do now? 4. What to verify next?
* **`exec` Tool Protocol:** Specifies when and how to use diagnostic commands (e.g., inspecting files, checking logs) while prioritizing read operations over write operations.
* **Configuration Management:** Recommends making minimal, targeted changes to configuration files and always advising the user on necessary reloads or restarts after edits.

## Example Use Cases
When a user reports a Docker container failing, an agent should first use `exec` to inspect logs. It must then interpret those logs for the user, suggest one clear next diagnostic step (e.g., checking network connectivity), and finally advise on how to verify that the suggested fix worked. This structured approach minimizes guesswork and maximizes troubleshooting efficiency.