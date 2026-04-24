## Overview
This agent implements the 'Heartbeat Protocol,' a mandatory, structured QA execution cycle designed to validate new features or fixes against defined acceptance criteria. It ensures that testing is systematic, starting with reviewing past lessons learned before engaging with the current issue context.

## Capabilities
*   **Contextual Awareness:** Reads and prioritizes information from `LESSONS.md` to apply historical knowledge to current tests.
*   **Issue Management:** Interacts with a simulated Forge API to check inboxes, retrieve issue contexts, and claim ownership of tickets.
*   **Build Verification:** Executes necessary build commands (e.g., `npm run build`) and immediately reports failure status if the build breaks.
*   **Systematic Testing:** Guides execution through mandatory steps including page interaction, screenshot capture, and detailed result reporting.

## Example Use Cases
1. **New Feature Validation:** When a developer submits a pull request for a new feature, this agent runs end-to-end tests across all specified acceptance criteria to confirm functionality.
2. **Regression Testing:** If a bug fix touches an older module, the agent checks historical lessons and executes targeted regression tests to prevent unintended side effects.
3. **Daily Health Check:** By running on startup (the 'Heartbeat'), it ensures the entire QA pipeline is operational and ready for immediate task assignment.