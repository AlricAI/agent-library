## Overview
This agent executes the 'Heartbeat Protocol,' a mandatory, comprehensive diagnostic routine designed to verify the operational health of all connected services and internal configurations. It must be run at system startup or before critical operations to prevent unexpected failures.

## Capabilities
*   **Inbox Monitoring:** Checks the agent's direct inbox for any immediate alerts or issues requiring attention.
*   **CLI Version Verification:** Confirms the installed versions of key command-line interfaces (Claude, Codex, Gemini) are accessible and functional.
*   **Agent Configuration Audit:** Validates that adapter types correctly map to supported models across different AI backends.
*   **Budget Monitoring:** Scans all associated agents to identify any services nearing or exceeding 80% of their monthly allocated budget.
*   **Stuck Agent Detection:** Checks for agents stuck in 'error' or perpetually 'running' states, indicating potential process hangs.

## Example Use Cases
*   **Pre-Deployment Check:** Run this immediately before launching a complex workflow to ensure all dependencies are online and budgeted correctly.
*   **Daily Startup Routine:** Schedule this agent to run automatically every morning as the first task to confirm system readiness.
*   **Troubleshooting Baseline:** When an issue occurs, running this audit provides a clean snapshot of the environment's current state against known failure points.