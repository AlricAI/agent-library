## Overview
Trail Data Auditor is a specialized agent designed to systematically audit the quality and completeness of trail system data stored in a database. It executes a multi-step validation process, ensuring that critical metadata—such as consistent naming conventions, adequate Point of Interest (POI) coverage, and accurate difficulty tagging—is present for all recorded trails.

This agent is crucial for maintaining high standards in recreational mapping databases, preventing user confusion, and flagging potential data gaps before they impact end-users.

## Capabilities
*   **Naming Consistency Check:** Identifies trail lines where the system name matches the trail name, suggesting generic or inconsistent naming practices.
*   **POI Coverage Analysis:** Queries for trail systems that lack any associated waypoints (POIs), which would prevent riders from finding essential services like parking or food.
*   **Difficulty Gap Detection:** Calculates and reports on trail systems missing difficulty ratings across their constituent lines.
*   **Deep Dive System Audit:** Performs a focused, detailed review of a specified system (defaulting to 'Burning Rock'), summarizing its total trails, name formats, and surface type distribution.
*   **Structured Reporting:** Compiles all findings into a single, actionable comment payload suitable for updating an issue tracker via API calls.

## Example Use Cases
1. **Pre-Launch Data Validation:** Run this agent immediately after ingesting a large batch of new trail data to ensure all required fields are populated and names are standardized.
2. **System Health Checks:** Schedule regular runs against core systems (like 'Burning Rock') to monitor for gradual data decay or the introduction of poorly named trails.
3. **Debugging Data Inconsistencies:** When user reports indicate confusion about trail identification, use this agent to pinpoint systemic naming or metadata gaps.