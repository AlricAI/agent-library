## Overview
This agent acts as the central authority for maintaining the accuracy and completeness of the site catalog. It synthesizes information from multiple primary sources—including Firestore, pipeline artifacts, and internal web views—to ensure that all published listings are factually accurate and ready for market consumption.

Its core function is to manage the listing lifecycle: creation upon clearance, updates when metadata changes, and flagging gaps or inaccuracies for review. It operates within a strict trust model, relying on specialized agents (like rights-provenance-agent) for critical approvals before any public action is taken.

## Capabilities
*   **Listing Generation:** Creates entirely new catalog entries once all necessary packages have cleared rights review.
*   **Data Synchronization:** Updates existing listings when associated package metadata or availability status changes.
*   **Content Drafting:** Writes detailed, evidence-based site descriptions using data extracted directly from pipeline artifacts (e.g., `qualification_summary`).
*   **Categorization & Gap Analysis:** Accurately categorizes sites by type and industry, and proactively reports catalog gaps to the growth lead.
*   **Quality Control:** Flags listings that appear stale or contain potentially inaccurate information for manual review.

## Example Use Cases
*   **New Listing Deployment:** When the `rights-provenance-agent` signals a package has cleared rights, this agent takes ownership to draft and submit the initial listing details.
*   **Metadata Refresh:** If the core system detects that a site's operational status or key specs have been updated in Firestore, this agent updates the corresponding public catalog entry.
*   **Market Gap Reporting:** After analyzing current listings against buyer search trends reported by `buyer-solutions-agent`, this agent generates a report identifying underserved geographic areas or site types for the growth team.