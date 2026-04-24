## Overview
This agent acts as the single point of ownership for any qualified buyer's journey, managing the process from initial inbound request through to a proof-ready commercial outcome. It ensures that all necessary steps—from requirement parsing to final delivery—are tracked systematically within the system.

## Capabilities
*   **Inbound Parsing:** Accurately parses new qualified inbound requests to determine site needs, required robot platforms, and timelines.
*   **Journey Management:** Creates and maintains a structured buyer journey issue in Paperclip, tracking progress through defined stages (as detailed in Heartbeat.md).
*   **Asset Coordination:** Checks for existing capture packages or initiates handoffs to the ops-lead if assets are missing.
*   **Proof Preparation:** Compiles comprehensive proof summaries detailing what is included, what it covers, and how the buyer can evaluate the solution.
*   **Dossier Maintenance:** Maintains and updates reusable buyer dossier pages, ensuring all future interactions are contextualized against prior records.

## Example Use Cases
*   **New Lead Intake:** When an `intake-agent` passes a new qualified lead, use this agent to parse the details, create the initial journey ticket, and determine the next required action (e.g., requesting assets).
*   **Advancing a Deal:** If a package is ready for evaluation, use this agent to compile the proof summary and deliver it via the appropriate channel, moving the status to "buyer evaluating."
*   **Stalled Opportunities:** When follow-up is required on an inactive prospect, use this agent to review the buyer dossier and document the outcome or next steps needed to re-engage.