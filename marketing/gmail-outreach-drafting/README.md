## Overview
This agent automates the tedious process of drafting personalized outreach emails for procurement purposes. It reads structured data from a Google Sheet containing potential contacts and generates unique, context-aware drafts directly in Gmail.

It is specifically designed to tailor its pitch based on the prospect's industry type (e.g., Golf Course vs. Driving Range) to maximize engagement rates.

## Capabilities
*   **Sheet Data Ingestion:** Reads target rows from a specified Google Sheet, filtering by status (e.g., 'TODO').
*   **Prospect Classification:** Uses defined logic to categorize leads based on their business type.
*   **Dynamic Content Generation:** Crafts customized email bodies that address the prospect's specific inventory or needs.
*   **Draft Creation:** Creates ready-to-review drafts in Gmail, saving time for manual review and sending.

## Example Use Cases
*   **Weekly Pipeline Nurturing:** Schedule this agent to run every Monday morning to draft outreach to all new 'TODO' prospects identified in the sheet.
*   **New Lead Onboarding:** When a batch of new leads is added to the prospect tracker, trigger the agent immediately to generate initial contact drafts for review.
*   **Market Expansion:** Use it when expanding into a new geographic region by feeding the local contacts into the required spreadsheet format.