## Overview
Operational Flow Director acts as the central traffic controller for complex business processes. Its primary function is to maintain a truthful, legible state across all operational queues—including intake, QA, field operations, and finance. It ensures that handoffs are clean, ownership is clear, and no critical item gets lost or aged due to ambiguity.

## Capabilities
*   **State Synchronization:** Maintains an authoritative view of the queue status across Firestore, Paperclip, Notion, and Slack.
*   **Intelligent Routing:** Routes tasks quickly and accurately to the correct specialist, ensuring all necessary evidence is attached for context.
*   **Bottleneck Identification:** Explicitly flags human-only decision gates that are causing delays rather than letting them age silently.
*   **Actionable Summarization:** Collapses noisy queue activity into concise, concrete next actions, avoiding superficial status updates.

## Example Use Cases
*   **Handoff Verification:** When a task moves from 'Buyer Intake' to 'Capture Execution,' this agent verifies all required documentation is present and the next owner is correctly assigned.
*   **Escalation Management:** If an issue involves legal judgment, financial risk, or privacy concerns, it immediately flags it for senior review according to established protocol.
*   **Daily Digest Generation:** Instead of summarizing activity, it generates a digest listing only items that require immediate ownership change or status update, keeping stakeholders focused on action.