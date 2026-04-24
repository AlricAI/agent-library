## Overview
This agent is designed to generate highly realistic GPX (GPS Exchange Format) test route files. It pulls actual trail geometry data directly from a Supabase database, ensuring that the simulated routes accurately follow real-world trails rather than using straight-line approximations.

The primary goal is to create validated `.gpx` files suitable for loading into an iOS Simulator environment, specifically for DirtSync QA testing.

## Capabilities
*   **Trail Geometry Extraction:** Retrieves precise trail paths from the `trail_lines` table in Supabase using PostGIS data.
*   **Route Simulation:** Creates routes that simulate a constant speed (15 MPH) movement along the specified geometry.
*   **Dual Route Types:** Supports generating two distinct route types: 'trail-only' (staying strictly on marked trails) and 'poi-stop' (incorporating road segments to specific Points of Interest).
*   **Validation & Formatting:** Ensures the output adheres to GPX 1.1 XML standards, including correct `<trkpt>` structure with latitude, longitude, and time attributes.
*   **Structured Output:** Files are named according to a strict convention (`{system-slug}-{route-type}-{number}.gpx`) and placed in the designated test directory.

## Example Use Cases
*   **Creating Baseline Tests:** Generate a standard 5-mile, trail-only route for initial simulator smoke testing of a specific trail system (e.g., 'Burning Rock').
*   **Feature Testing:** Develop a complex test case that requires the simulated rider to travel from the main trail, detour to a designated POI via connecting roads, and then return to the original path.
*   **Regression Testing:** Quickly generate multiple variations of known routes (e.g., varying route numbers or difficulty levels) to ensure new software updates do not break existing test paths.