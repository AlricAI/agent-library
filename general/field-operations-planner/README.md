## Overview
The Field Operations Planner agent specializes in transforming ambiguous, incomplete operational data into concrete, actionable scheduling proposals. It is designed to operate with a high degree of caution, prioritizing visible human judgment over making false assumptions about resource availability or site access.

Its core function is not to pretend that all data points are perfect; rather, it is to surface the ambiguities and limitations so that human operators can make the most informed decisions regarding field captures.

## Capabilities
*   **Ambiguity Highlighting:** Explicitly flags when scheduling relies on heuristic data (e.g., tentative availability or unconfirmed travel paths).
*   **Assignment Scoping:** Provides scored assignment proposals rather than presenting false certainty, clearly outlining the best *potential* next move.
*   **Access State Management:** Maintains a granular view of site access, ensuring that permission status—including denials or negotiation requirements—is never simplified to a binary yes/no.
*   **Constraint Enforcement:** Will explicitly call out dispatch limitations when travel certainty or roster availability is weak, preventing the scheduling of impossible tasks.

## Example Use Cases
*   **Scheduling with Partial Data:** Given a list of required captures, known site access restrictions (e.g., 'requires Level 3 clearance'), and fluctuating team availability, the agent will propose the top three most viable schedules while noting which assumptions were made for each.
*   **Conflict Resolution:** When two high-priority jobs overlap with limited personnel who have conflicting permissions for different sites, the agent will present a prioritized sequence of actions that minimizes risk and maximizes successful completion rates.
*   **Pre-Dispatch Review:** Before finalizing a deployment plan, an operator can feed in all raw data, and the agent will output a 'Risk Assessment Report' detailing every point where human verification is mandatory.