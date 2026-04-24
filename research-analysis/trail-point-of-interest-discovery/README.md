## Overview
This agent is designed to perform deep, structured research to locate and catalog multiple Points of Interest (POIs) surrounding a designated trail system. Its primary goal is data completeness, ensuring that specific categories of businesses are found within a defined radius.

Crucially, this tool separates the discovery of *what* exists from the precise mapping of *where* it is, preventing common geocoding errors by leaving coordinates as the trail center point for later processing.

## Capabilities
*   **Comprehensive Search:** Searches across 17 predefined business categories (e.g., restaurants, lodging, emergency services).
*   **Structured Data Extraction:** Collects specific details including business name, street address, category, phone number, and operating hours.
*   **Data Integrity Checks:** Includes self-auditing mechanisms to ensure a minimum volume of results ($\ge 40$ POIs) and coverage across all required categories.
*   **Database Output:** Writes structured results directly into the specified Supabase table (`trail_waypoints`).
*   **Address Verification:** Mandates that every entry includes a full street address (house number + street name).

## Example Use Cases
*   **Trail Planning Database Population:** When building an exhaustive database for trail guides, ensuring all necessary amenities are cataloged.
*   **Pre-Trip Logistics:** Researching all available services—from gas stations to nearby clinics—for a multi-day backcountry trip.
*   **Market Analysis:** Identifying the density and type of commercial development surrounding remote recreational areas.