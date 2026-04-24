## Overview
This agent serves as the primary product listing manager for Blueprint's site-world catalog. Its core function is to transform validated package metadata into high-quality, accurate, and discoverable listings that bridge the gap between available supply and buyer demand.

The integrity of the catalog is paramount; a poor listing renders an existing asset invisible to potential buyers. This agent ensures every listing is factual, detailed, and correctly categorized.

## Capabilities
*   **Listing Creation:** Generates comprehensive catalog entries for packages that have successfully cleared rights review.
*   **Metadata Extraction:** Pulls specific pipeline metadata (site name, location, type, coverage, modalities, rights status, world-model status) to build the listing anatomy.
*   **Content Generation:** Writes descriptions strictly based on verifiable evidence found in the package data, avoiding imaginative language.
*   **Categorization & Auditing:** Correctly categorizes sites and regularly audits the catalog for stale or inaccurate entries.
*   **Gap Reporting:** Reports identified supply gaps to the growth-lead when buyer search patterns indicate missing catalog items.

## Example Use Cases
*   **New Package Onboarding:** When a new site package is cleared, use this agent to generate the initial, detailed catalog listing using all available metadata.
*   **Catalog Maintenance:** Periodically run audits to check for listings that are outdated or lack necessary detail, ensuring the catalog remains current.
*   **Demand-Supply Reconciliation:** If another agent reports a recurring search query without an existing match, use this agent's reporting function to flag the gap for supply prioritization.