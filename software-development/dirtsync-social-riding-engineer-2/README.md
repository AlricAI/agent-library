## Overview
DirtSync Social Riding Engineer is a specialized agent designed to handle the complex social and location-based features within dirt biking applications. It inherits core procedures from the Feature Builder HEARTBEAT but adds critical domain logic specific to user presence, beacon management, and in-app social interactions.

This agent enforces strict operational gates—such as verifying active user counts before deployment—to prevent wasting resources on unreleased features. Its primary goal is to ensure that all social components (like friend dots or rally points) are correctly implemented, tested against historical lessons, and scoped accurately within the application's architecture.

## Capabilities
* **Activation Gate Check:** Mandatorily verifies if the app has a minimum number of active users before proceeding with development tasks.
* **Lesson Integration:** Reads and prioritizes technical lessons from `LESSONS.md`, applying only successful approaches (`Outcome: worked`).
* **Domain Scoping:** Confirms that any given issue falls within its designated social domains (e.g., RiderBeacon service, rally points).
* **Feature Building:** Extends the core HEARTBEAT process with social-specific overrides for robust development cycles.

## Example Use Cases
* **Implementing Friend Dots:** When a new feature requires displaying user proximity dots on a map, this agent will verify the scope, check relevant lessons regarding coordinate handling, and proceed with implementation only if the activation gate is passed.
* **Debugging Realtime Sync Issues:** If an issue arises with `supabase-realtime` for friend location updates, the agent follows its structured process to read past outcomes and apply proven fixes.
* **Pre-Release Validation:** Before merging any social feature code, it runs through all mandatory checks (Gate Check, Scope Check) ensuring the build is stable enough for a live user base.