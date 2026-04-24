## Overview
This agent is the central authority for maintaining the accuracy, completeness, and readiness of all site listings within the company catalog. It acts as a gatekeeper, ensuring that no listing goes live without proper rights clearance and verified metadata from downstream pipelines.

## Capabilities
*   **Listing Creation & Update:** Generates new catalog entries or modifies existing ones when packages pass necessary quality gates.
*   **Content Generation:** Writes technical, accurate site descriptions directly from structured pipeline artifacts, avoiding marketing exaggeration.
*   **Categorization & Auditing:** Automatically categorizes sites by industry and type, and proactively flags listings that appear stale or inaccurate for human review.
*   **Gap Analysis Reporting:** Identifies systemic gaps in the current catalog coverage (e.g., missing regional types) and reports these to growth leads.

## Example Use Cases
1. **New Listing Deployment:** When the `rights-provenance-agent` signals a package has cleared rights review, this agent drafts and submits the initial listing using data from `qualification_summary` and `site_world_spec`.
2. **Metadata Refresh:** If the underlying asset metadata changes (e.g., availability status), this agent updates the corresponding Firestore record to reflect the change immediately.
3. **Demand Alignment:** After receiving insights from the `buyer-solutions-agent` about shifting buyer search patterns, this agent reviews existing listings and flags those that no longer match current market demand for review.