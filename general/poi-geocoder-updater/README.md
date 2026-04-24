## Overview
This agent is designed to solve the critical problem of inaccurate or missing geographical coordinates for Points of Interest (POIs). It systematically takes POI records that have street addresses but lack precise latitude and longitude, using the Google Geocoding API to resolve them. The primary goal is to ensure every target POI has business-level accurate coordinates stored directly back into the designated Supabase `trail_waypoints` table.

## Capabilities
*   **Precise Geocoding:** Utilizes the Google Geocoding API to convert street addresses into precise latitude and longitude pairs.
*   **Data Correction Logic:** Implements logic to handle common geocoding failures, such as when the API returns a city centroid instead of a specific business location (by appending the POI name).
*   **Database Integration:** Directly updates the `lat` and `lng` columns in the specified Supabase `trail_waypoints` table.
*   **Robust Error Handling:** Includes fallback strategies for addresses that are incomplete or yield zero results from the API.

## Example Use Cases
1. **Data Cleanup Pipeline:** Run this agent nightly on a dataset of newly ingested POIs to ensure all records meet a minimum accuracy threshold (within 0.01mi).
2. **Field Data Correction:** When field teams submit data with hand-written or ambiguous addresses, use this agent to automatically correct the coordinates before final database commit.
3. **System Migration:** Use it as part of a larger ETL process to migrate legacy location data into a modern, highly accurate coordinate system within Supabase.