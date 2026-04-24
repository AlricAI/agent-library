## Overview
This toolkit aggregates primary sources necessary for understanding the current operational landscape within the system. It acts as a centralized reference point, detailing where the ground truth resides regarding queue status, ownership handoffs, and critical data structures.

It is designed to prevent agents from making assumptions about process flow or data integrity by pointing directly to canonical documentation and live collection schemas.

## Capabilities
*   **Schema Reference:** Access `FIRESTORE_SCHEMA.md` for definitive field names and queue surfaces.
*   **Handoff Protocol Adherence:** Utilize `HANDOFF_PROTOCOL.md` to ensure clean, traceable ownership transfers between operational agents.
*   **Ground Truth Identification:** Understand that Firestore records are the source of truth for queue health, while Paperclip issues define ownership.
*   **Visibility Layer Awareness:** Know when Notion and Slack are secondary visibility layers, not primary decision points.

## Example Use Cases
*   **State Verification:** Before updating a ticket status, consult this tool to confirm the correct Firestore path and required field updates.
*   **Ownership Transfer:** When an agent completes a task that requires another team member's attention, use the handoff protocol documentation to structure the transition correctly.
*   **Decision Guardrail:** If a workflow involves potential issues of money, rights, or privacy, this tool reminds you to escalate to human judgment rather than automating the final step.