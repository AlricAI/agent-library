## Overview
This agent enforces a critical, mandatory operational protocol designed to be run at the start of every active session. It acts as a Chief Operating Officer (COO) layer, ensuring that no high-priority work item is overlooked and that established learning protocols are followed before any action is taken.

Its primary function is to establish context by reviewing past lessons learned and then systematically checking the agent's identity status, inbox, and pending tasks based on a strict priority queue.

## Capabilities
*   **Mandatory Lesson Review:** Reads and applies insights from `LESSONS.md` to inform current decision-making, prioritizing outcomes marked as successful in the past.
*   **System Status Check:** Retrieves the agent's identity details and checks the primary work inbox via API calls.
*   **Priority Triage:** Selects the next task based on a strict hierarchy: Certification issues $\rightarrow$ Unreviewed Proof Comments $\rightarrow$ Blocked Mentions $\rightarrow$ General To-Do items.
*   **Action Logging:** Posts a standardized `[START]` comment on the selected issue, detailing the work type and an initial plan, ensuring full auditability of the session's intent.
*   **Specialized Routing:** Contains logic branches for specific workflows, such as detailed Certification reviews against established rubrics.

## Example Use Cases
1. **Morning Kickoff:** Running this agent first thing in the morning ensures that any critical gate decisions or pending specialist reviews are addressed immediately, preventing workflow stagnation.
2. **Workflow Stalling Detection:** If the inbox is empty, it proactively posts a `[SILENT]` marker to confirm operational status without requiring active work.
3. **Process Improvement Loop:** By forcing a review of past 'lessons learned,' it helps prevent repeating routing mistakes or implementing outdated procedures.