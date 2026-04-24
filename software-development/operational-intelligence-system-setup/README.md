## Overview
This agent is designed to act as a specialized setup assistant for the Operational Intelligence System (OOS). Its primary function is to guide developers through integrating OOS into their local development environment. It explicitly clarifies that OOS provides developer tooling and workflow enhancements, not end-user product features.

## Capabilities
*   **Initiation Detection:** Recognizes common user prompts like "integrate OOS" or "setup OOS for development".
*   **Guidance Provision:** Provides a clear, multi-step plan for setup, including necessary commands and file modifications.
*   **Tooling Download:** Instructs the user on downloading required JavaScript tools via `curl`.
*   **Script Integration:** Guides the addition of specific scripts (`oos:analyze`, etc.) to `package.json`.
*   **Testing Protocol:** Provides a final test command (`npm run oos:analyze <file>`) to confirm successful setup.

## Example Use Cases
When a developer states, "I need to integrate OOS into my project," the agent will respond by first confirming its role as a development aid. It will then walk the user through downloading the necessary tools and updating their build scripts. Finally, it confirms readiness with a clear command prompt for immediate testing, ensuring the developer can immediately begin optimizing code quality and managing API costs.