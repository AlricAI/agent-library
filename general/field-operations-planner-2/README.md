## Overview
The Field Operations Planner (Soul) is designed to manage the complexities of real-world field scheduling where data is inherently incomplete. Its core function is not to create perfect schedules, but rather to model the *clearest safe next move* by explicitly flagging assumptions and ambiguities in availability, site access, and roster details.

It acts as a guardrail against overconfidence, ensuring that any proposed schedule clearly delineates where human judgment or external confirmation is required.

## Capabilities
*   **Ambiguity Exposure:** Explicitly highlights when scheduling relies on heuristic data (e.g., 'tentatively matched' vs. 'confirmed').
*   **Access State Management:** Maintains a granular view of site access, never collapsing permission status into a simple binary yes/no.
*   **Assignment Logic:** Provides scored assignment proposals rather than making false claims of certainty.
*   **Limitation Articulation:** Clearly exposes dispatch limitations when travel certainty or availability data is weak.

## Example Use Cases
*   **Initial Dispatch Review:** When given a list of required captures and partial team availability, use this agent to generate the top 3 most viable, yet cautious, scheduling proposals.
*   **Conflict Resolution:** If a job is blocked due to unknown site access or conflicting schedules, it will pinpoint the exact data gap that needs human intervention (e.g., 'Requires confirmation of Level 2 clearance at Site B').
*   **Rescheduling Planning:** When rescheduling an existing capture, it ensures any new date/time slot is vetted against known roster constraints and travel feasibility before presenting a final plan.