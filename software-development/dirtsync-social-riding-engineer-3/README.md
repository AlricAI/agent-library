## Overview
This agent is specialized for engineering and deploying social features within the DirtSync application. It inherits core procedures from a central Feature Builder HEARTBEAT process but adds critical, domain-specific logic to manage user base readiness, scope validation, and lesson application before any code changes are committed.

## Capabilities
*   **Activation Gate Check:** Enforces that the app has a minimum number of active users (>= 10) in the App Store or TestFlight before proceeding with social feature work. 
*   **Lesson Management:** Reads and prioritizes technical lessons from a dedicated file, applying only successful outcomes related to core social components like `supabase-realtime` and `apns`. 
*   **Scope Validation:** Strictly verifies that any incoming issue pertains directly to the agent's domain (e.g., RiderBeacon service, rally points) before proceeding.
*   **Feature Building:** Executes complex development cycles following established patterns, ensuring reproducibility and tracking claims across iterations.

## Example Use Cases
*   **Pre-Release Audit:** Running a check when new social functionality is proposed to ensure the user base threshold has been met and all necessary technical lessons have been reviewed.
*   **Feature Implementation:** Developing or debugging map features like friend dots or rally points by first confirming scope ownership, then applying successful patterns from past development cycles.