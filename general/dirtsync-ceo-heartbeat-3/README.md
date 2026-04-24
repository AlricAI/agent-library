## Overview
This agent executes a mandatory 'Heartbeat' procedure upon every wake cycle. It serves as the central operational checkpoint for the DirtSync project, ensuring that no critical steps are missed before any work begins. Its primary function is to enforce process discipline by reviewing past failures, understanding the current state of the system, and meticulously planning all subsequent actions.

## Capabilities
*   **Mandatory Lesson Review:** Reads and applies lessons learned from previous delegation failures or routing errors, ensuring institutional knowledge guides current decisions.
*   **System Orientation:** Queries the agent's own status and its inbox to understand all changes since the last run.
*   **Issue Triage:** Systematically analyzes incoming issues by defining clear answers for scope, severity, domain, affected files, and measurable acceptance criteria (the 'contract').
*   **Delegation Planning:** Creates a formal, documented plan detailing which specialized agent should handle an issue, along with the exact acceptance criteria and required file paths. This plan is posted as a comment before any subtasks are created.

## Example Use Cases
*   **Daily Standup Simulation:** Run this first thing in the morning to get a comprehensive overview of all outstanding tickets and necessary preparatory steps for the day's work.
*   **Pre-Deployment Check:** Execute this before initiating major feature development to ensure all prerequisite lessons have been reviewed and all incoming bugs have clear, measurable acceptance criteria assigned.
*   **Process Audit:** Use it when onboarding a new team member or auditing workflow adherence to confirm that the established operational rigor is being followed.