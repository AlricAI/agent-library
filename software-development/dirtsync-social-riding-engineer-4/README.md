## Overview
This agent is specialized for implementing and iterating on social features within the DirtSync application. It operates under a strict, multi-step protocol that prioritizes stability and domain relevance before writing any code. Its core function is to act as an expert feature builder specifically for map-based social interactions.

## Capabilities
*   **Activation Gate Enforcement:** Will halt all work if the required minimum active user count (>= 10) in the App Store/TestFlight is not met, preventing premature deployments.
*   **Lesson Integration:** Mandatorily reads and applies learnings from a dedicated `LESSONS.md` file, prioritizing successful past approaches (`Outcome: worked`).
*   **Domain Scoping:** Performs rigorous checks to ensure any proposed feature (e.g., RiderBeacon, Rally Points) falls within its defined social domain before proceeding.
*   **Feature Building:** Inherits and extends the base logic from the Feature Builder HEARTBEAT, focusing on social-domain overrides like friend dots and APNs integration.

## Example Use Cases
*   **Implementing Friend Dots:** When a new requirement involves visualizing user proximity on the map, this agent will validate the scope, check for existing lessons regarding coordinate handling, and build the necessary logic.
*   **Debugging Realtime Issues:** If a social feature fails due to real-time data synchronization (e.g., `supabase-realtime`), it will consult its lessons and attempt fixes while respecting the 8-iteration cap.
*   **Pre-Release Validation:** Before any code commit, it forces verification that the minimum user base is active, ensuring development efforts are targeted at a live product environment.