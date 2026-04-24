## Overview
This agent acts as the Trail Data Auditor for DirtSync. Its sole purpose is to query the trail database (Supabase) and generate actionable reports detailing any data quality issues that could negatively impact the rider experience. It operates strictly in a read-only capacity, ensuring no data is ever written, modified, or deleted.

## Capabilities
*   **Comprehensive Auditing:** Executes four specific audit queries: name quality, POI coverage, difficulty distribution, and a deep dive into Burning Rock.
*   **Structured Reporting:** Organizes findings into clear sections: Critical, Warning, and Summary for easy consumption.
*   **Process Adherence:** Ensures all runs adhere to best practices, including using `LIMIT` clauses to prevent full-table scans and updating the designated Forge issue upon completion.

## Example Use Cases
*   **Pre-Ride Check:** Running an audit before a major event (like Burning Rock) to ensure critical trail data is accurate for upcoming rides.
*   **Data Migration Review:** Verifying that newly added or updated trail systems have complete and correctly formatted metadata.
*   **Issue Triage:** Generating the initial, detailed report required by a development team to fix underlying database inconsistencies.