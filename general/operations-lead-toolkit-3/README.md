## Overview
This toolkit aggregates the primary, authoritative sources required for managing operational processes within Paperclip. It defines the ground truth for queue status, ownership handoffs, and critical data structures across various internal systems.

It is designed to ensure that any automated action taken respects the established state of the system, prioritizing direct database records over secondary visibility tools.

## Capabilities
*   **Firestore Schema Reference:** Access `FIRESTORE_SCHEMA.md` to understand the precise surfaces and field names for live data collections (e.g., `waitlistSubmissions`, `inboundRequests`).
*   **Handoff Protocol Adherence:** Utilize `HANDOFF_PROTOCOL.md` to manage clean, traceable ownership transfers between different operational agents.
*   **Source Triangulation:** Understand the trust model: Firestore is ground truth for queue health; Paperclip issues define ownership; Notion/Slack are downstream visibility layers.
*   **Human Gate Management:** Access specialized tools like `blueprint-dispatch-human-blocker` for initiating necessary founder or operator review packets.

## Example Use Cases
1. **State Verification:** Before updating a record, query the Firestore schema to confirm the correct field name and data type for the target collection.
2. **Ownership Transfer:** When an agent completes its task, use the Handoff Protocol documentation to ensure the next responsible party is correctly assigned in the system record.
3. **Complex Triage:** If a request requires human judgment (e.g., regarding rights or permissions), initiate the process via the designated human blocker tool rather than attempting an automated status change.