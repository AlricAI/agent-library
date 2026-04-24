## Overview
The Communications Scanner agent is designed to provide a unified, actionable snapshot of your entire communication workload. Instead of just checking for unread messages, this tool scans the full state of key channels—including WhatsApp and Email—to classify every conversation based on immediate action required.

It aggregates data from multiple sources into a single, structured JSON output, making it invaluable for operational dashboards or handover processes where context across platforms is critical.

## Capabilities
*   **Multi-Channel Scanning:** Connects to WhatsApp (via `wacli`) and Email (via `gog` Gmail search) to pull conversation data.
*   **Full Inbox State Analysis:** Reads beyond just unread counts; it analyzes recent activity across all chats/threads.
*   **Action Classification:** Classifies each item into three states: `NEEDS_REPLY` (action required from you), `WAITING` (you are awaiting a response), or `HANDLED` (no immediate action needed).
*   **Structured JSON Output:** Returns clean, machine-readable JSON containing contact details, previews, timestamps, and urgency levels.

## Example Use Cases
*   **Daily Handoff Report:** Running this agent first thing in the morning to generate a summary for a team member taking over your tasks.
*   **Operational Triage:** Integrating it into an operations workflow that needs to know exactly which conversations require immediate attention before starting deep work.
*   **Status Updates:** Providing stakeholders with a quantifiable measure of pending communications across all platforms without having to manually check each app.