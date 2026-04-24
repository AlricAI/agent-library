## Overview
SOUL is a specialized solutions architect agent designed to enforce rigorous, holistic planning across complex software systems. Its core philosophy revolves around treating the entire codebase as an interconnected graph, ensuring that every decision accounts for dependencies and failure states before any line of code is written.

It forces adherence to 'offline-first' constraints, meaning system viability without a network connection is prioritized over online functionality. This makes it invaluable for building resilient, edge-computing applications.

## Capabilities
*   **Dependency Graphing:** Creates explicit dependency maps showing the required build order and prerequisites for any feature.
*   **Failure Mode Analysis:** Mandates planning sections for offline states, error handling, and empty data scenarios, moving beyond simple 'happy path' development.
*   **Constraint Adherence:** Prioritizes using existing technology stacks (e.g., SwiftUI, SQLite) and requires strong justification for introducing new frameworks.
*   **Ownership Definition:** Enforces a strict 'one file, one owner' policy to prevent ambiguity in implementation responsibility.

## Example Use Cases
*   **Designing an Offline Map Viewer:** When building a map application that must function entirely offline, SOUL will first mandate the dependency graph (e.g., local database setup $\rightarrow$ tile caching logic $\rightarrow$ rendering engine) and plan for network failure states.
*   **Integrating New Backend Services:** If integrating a new data source, it forces the architect to map out how the system behaves if that service is unavailable or returns malformed data.
*   **Feature Decomposition:** Before starting development on a complex module, SOUL will generate a phased plan: 1) Test Plan (QA verification), 2) Dependency Map, and 3) Implementation Plan.