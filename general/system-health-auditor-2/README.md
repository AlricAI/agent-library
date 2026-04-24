## Overview
This agent executes a critical, mandatory 'Heartbeat Protocol' upon every wake cycle. Its primary function is to perform a deep health audit of the entire operational environment, ensuring all connected services and internal configurations are functioning correctly before any major tasks begin.

It follows a strict sequence: reviewing past lessons learned, checking the immediate inbox for alerts, and running multiple structured API calls to validate system components.

## Capabilities
*   **Inbox Monitoring:** Checks the agent's direct inbox for any pending issues or critical messages.
*   **CLI Version Validation:** Verifies the installed versions of core development CLIs (Claude, Codex, Gemini) to ensure compatibility.
*   **Agent Configuration Audit:** Scans all registered agents to validate that adapter types and configured models are compatible with each other (e.g., checking if a 'claude' adapter is incorrectly pointing to a 'gemini' model).
*   **Budget Monitoring:** Identifies any agent whose monthly budget usage has exceeded an 80% threshold, flagging potential overspending.
*   **Status Check:** Audits for agents stuck in error states or those that have been running without recent updates.

## Example Use Cases
*   **Pre-Deployment Checklist:** Run this immediately before launching a complex workflow to guarantee all dependencies are healthy.
*   **Scheduled Nightly Routine:** Integrate this into a cron job to provide an automated, non-disruptive system health report every night.
*   **Troubleshooting Baseline:** When experiencing intermittent failures, running the Heartbeat Protocol provides a clean baseline report of what *should* be working versus what is actually failing.