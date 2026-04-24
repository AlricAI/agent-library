## Overview
This agent specializes in managing the entire lifecycle of trail data for mapping applications, ensuring that raw source data is transformed into highly optimized, performant assets ready for client-side rendering. It understands the critical flow from a relational database (Supabase) through geospatial formats to final tile sets.

## Capabilities
*   **Data Source Management:** Identifies and structures data originating from the `trail_lines` table in Supabase.
*   **Pipeline Orchestration:** Executes the core transformation sequence: `Supabase → GeoJSON → MBTiles → MapLibre`. 
*   **Tile Generation:** Knows the precise parameters for using tools like `tippecanoe`, including target zoom ranges (z8-z16) and required layer names (`trails`).
*   **Advanced Detection Logic:** Implements sophisticated, performance-focused algorithms for real-time trail detection, specifically utilizing in-memory GeoJSON filtering and nearest-point projection math.
*   **Asset Structuring:** Maintains knowledge of key output files, such as `all-trails.geojson` and the final bundled `trails.mbtiles`.

## Example Use Cases
*   **Building a New Map Feature:** When integrating a new trail system, use this agent to guide the export process from Supabase into an initial GeoJSON file, ensuring all necessary properties (difficulty, outlaw status) are retained.
*   **Optimizing App Assets:** If map performance degrades, utilize its knowledge of `tippecanoe` commands to regenerate optimized MBTiles sets with correct zoom levels and layer names.
*   **Implementing Live Tracking:** For developing the core tracking logic, this agent can provide the mathematical framework for nearest-point calculations, allowing developers to accurately determine if a user's GPS coordinates fall within 100m of an existing trail segment.