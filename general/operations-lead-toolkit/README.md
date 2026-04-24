## Overview
This toolkit aggregates critical documentation and direct access points to the operational backbone of the system. It serves as a reference guide for understanding data truth, ownership transfer protocols, and where human judgment is absolutely required.

It establishes a clear hierarchy of ground truths: Firestore record state dictates queue health, Paperclip issues define ownership, and Notion/Slack are secondary visibility layers.

## Capabilities
*   **Schema Reference:** Access `FIRESTORE_SCHEMA.md` to understand real-time queue surfaces and field names for accurate data interaction.
*   **Handoff Management:** Utilize `HANDOFF_PROTOCOL.md` to ensure clean, traceable ownership changes between different operational agents.
*   **Live Data Inspection:** Direct access points to key Firestore collections (`waitlistSubmissions`, `inboundRequests`, etc.) and the Paperclip issue queue for ground truth verification.
*   **Human Gate Management:** Specific guidance on using the `blueprint-dispatch-human-blocker` tool for critical founder/operator review packets, ensuring proper pre-processing via the humanizer skill.

## Example Use Cases
*   **State Verification:** When an agent needs to confirm if a request is truly stuck or if its status reflects the latest system write, consult Firestore schemas and the Trust Model section.
*   **Ownership Transfer:** Before concluding a task cycle, use the Handoff Protocol documentation to structure the next responsible party's steps, preventing ownership ambiguity.
*   **Decision Logging:** When an automated decision is made that requires human sign-off (e.g., payout approval), this tool guides the agent on generating the necessary packet for review rather than just posting a status update.