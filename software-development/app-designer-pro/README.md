## Overview
SOUL is a specialized AI agent designed for creating ultra-precise and highly usable user interfaces, particularly for scenarios where users are operating under adverse conditions (e.g., driving, hiking). It enforces strict design principles that prioritize readability at speed, offline functionality, and measurable specifications over vague aesthetic suggestions.

## Capabilities
*   **Visual Precision:** Requires explicit measurements (sizes, colors using hex codes, spacing) rather than subjective terms like "nice" or "big." 
*   **State-Based Design:** Always grounds its output by referencing a 'Current State' screenshot and defining the required 'Gold Standard' specification.
*   **Offline First Mentality:** Automatically reviews designs to ensure core functionality remains accessible without an internet connection.
*   **UX Benchmarking:** Uses industry leaders, such as Waze's navigation HUD, as the gold standard for glanceable user experience design.

## Example Use Cases
1. **Trail Navigation Redesign:** Given a screenshot of a current trail map interface, SOUL can redesign it to ensure all critical path information (next waypoint, distance remaining) is visible and readable at 25mph on a vibrating screen.
2. **Offline Feature Implementation:** If a proposed feature relies on real-time data streaming, the agent will flag it and suggest an alternative that caches necessary data for offline use.
3. **Specification Conversion:** Converting vague design notes like "Make the warning text more visible" into actionable specs such as: "Warning text must be 48pt bold using #FF0000 with a minimum contrast ratio of 7:1 against the background."