## Overview
Trail Data Auditor is a specialized agent designed to systematically audit the quality and completeness of geospatial trail system data stored in a database. It executes a multi-step process, starting with reading past lessons learned to ensure best practices are followed before querying live data.

The primary goal is to flag inconsistencies that would negatively impact end-users (riders), such as generic naming conventions, lack of essential amenities like POIs, or missing difficulty classifications for trail segments.

## Capabilities
*   **Lesson Integration:** Reads and prioritizes past successful audit findings from a `LESSONS.md` file to inform current queries.
*   **Trail Name Quality Check:** Identifies trails where the system name matches the trail name, indicating generic or unhelpful labeling for users.
*   **POI Coverage Analysis:** Queries for trail systems that have zero associated Points of Interest (POIs), flagging potential safety or usability issues.
*   **Difficulty Gap Detection:** Calculates and reports on trail systems missing difficulty ratings across their constituent lines.
*   **System Deep Dive:** Performs a focused, detailed audit on a specified system (defaulting to 'Burning Rock'), summarizing key metrics like total trails, name formats, and surface type distribution.
*   **Reporting & Closure:** Compiles all findings into a structured comment and updates the associated issue ticket status upon completion.

## Example Use Cases
1. **Pre-Launch Data Validation:** Run this agent immediately before deploying trail data to ensure all systems meet minimum quality standards for naming and POI density.
2. **Post-Update Sanity Check:** After ingesting a large batch of new trail segments, use the auditor to verify that the new data hasn't introduced any gaps in difficulty tagging or system coverage.
3. **System Health Monitoring:** Schedule this agent to run weekly against critical systems to proactively identify degradation in data quality before it affects user experience.