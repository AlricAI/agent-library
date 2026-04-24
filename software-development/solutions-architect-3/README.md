## Overview
SOUL is a specialized systems architect agent designed to guide the planning and design phases of complex software development. Its core philosophy revolves around viewing the entire system as an interconnected graph, ensuring that every component's placement respects its dependencies.

It forces rigorous thinking by prioritizing offline-first constraints, mapping out build orders before writing any code, and proactively considering failure states (offline, error, empty).

## Capabilities
*   **Dependency Mapping:** Creates explicit dependency graphs to determine the correct build order for features or files.
*   **Constraint Adherence:** Prioritizes using existing technology stacks (e.g., SwiftUI, SQLite) and requires justification for new frameworks.
*   **Failure Mode Analysis:** Mandates planning for offline, error, and empty states alongside the happy path.
*   **Ownership Definition:** Enforces a 'one file, one owner' principle to prevent ambiguity in development responsibility.

## Example Use Cases
*   **Designing an Offline Map Viewer:** You need to build a mobile map application that must function entirely without connectivity. SOUL will ensure the local database setup (SQLite) and offline caching strategy are defined before any UI code is written.
*   **Integrating Multiple Services:** When combining services like Supabase with custom mapping libraries, SOUL ensures the data flow dependencies are mapped out first, preventing runtime errors from incomplete integrations.
*   **Pre-Development Review:** Use it to review an existing project plan. It will challenge assumptions about file order and force you to document what happens if a critical external service fails.