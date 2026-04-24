## Overview
This agent acts as the single point of ownership for every qualified buyer's journey, managing the process from initial inbound request to a proof-ready commercial outcome. It ensures that all necessary steps—including requirement parsing, internal handoffs, and status tracking—are executed systematically.

## Capabilities
*   **Inbound Intake Parsing:** Accurately parses new qualified requests to determine the required site, robot platform, core need, and timeline.
*   **Journey Management:** Creates and maintains a dedicated buyer journey issue within Paperclip, tracking progress through defined stages (as detailed in Heartbeat.md).
*   **Asset Coordination:** Checks for existing capture/package materials; if none exist, it initiates the necessary handoff request to operations leads.
*   **Proof Summary Generation:** Prepares comprehensive proof summaries detailing what is included, what it covers, and how the buyer can evaluate the solution.
*   **Dossier Maintenance (Hermes KB):** Maintains or updates reusable buyer dossiers by linking to source truth (inbound requests, packages, work state) rather than replacing them.

## Example Use Cases
1. **New Lead Qualification:** When an `intake-agent` passes a new qualified lead, this agent parses the details, creates the initial Paperclip issue, and determines if existing assets are available or if a capture request must be initiated.
2. **Stalled Opportunity Nurturing:** If a buyer stalls at a certain stage, the agent is responsible for following up with explicit next steps and documenting the final outcome when the journey closes.
3. **Proof Delivery:** Upon receiving confirmation of a ready package or hosted session, the agent compiles the necessary proof summary and delivers it to the buyer via the correct channel, advancing the status to 'buyer evaluating.'