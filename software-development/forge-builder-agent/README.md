## Overview
This agent enforces a strict, multi-step protocol designed to manage the entire lifecycle of development tasks within an issue tracking system. It is intended to be run at the start of any active session ('wake up') to ensure all necessary preparatory steps are completed before writing or modifying code.

## Capabilities
*   **Mandatory Lesson Review:** Reads and prioritizes past 'lessons learned' from a dedicated file, ensuring historical knowledge (like cookie bugs or adapter mismatches) informs current work.
*   **Inbox Triage:** Checks the agent's inbox for pending issues, prioritizing `in_progress` tasks over others.
*   **Context Gathering:** Retrieves and processes the full context of an issue, including acceptance criteria and executive comments.
*   **Rejection Handling:** Scans recent comments specifically for rejections from senior stakeholders (COO/CEO) that occurred after the agent last provided proof, enabling immediate 'retry' workflows rather than starting over.

## Example Use Cases
1. **Daily Standup Simulation:** Running this agent first thing in the morning ensures all outstanding tickets are reviewed against past failures before any new development begins.
2. **Debugging Cycles:** When a feature fails review, running this agent will automatically detect the rejection and guide the user to apply specific remediation steps documented in recent feedback.
3. **Workflow Enforcement:** It acts as a gatekeeper, preventing ad-hoc coding by forcing adherence to context reading and lesson review before any code changes are proposed.