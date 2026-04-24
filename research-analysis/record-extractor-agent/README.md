## Overview
The Record Extractor Agent is a deterministic tool designed specifically for high-fidelity, structured data extraction. Unlike general summarization agents, this agent's sole purpose is to parse raw text and return the information strictly adhering to a provided JSON schema.

It enforces strict rules—such as returning *only* data supported by evidence and omitting prose—making it ideal for integrating into automated workflows that require predictable, machine-readable output.

## Capabilities
*   **Schema Adherence:** Guarantees the output structure matches the required JSON schema precisely.
*   **Deterministic Output:** Optimized to return compact records with minimal extraneous text or markdown.
*   **Evidence-Based Extraction:** Only extracts data directly supported by the input document text.
*   **Handling Missing Data:** Gracefully handles missing information by omitting fields or returning null, preventing structural errors.

## Example Use Cases
*   **Invoice Processing:** Extracting line items, total amounts, and vendor details from scanned invoices into a standardized JSON format.
*   **Database Population:** Reading unstructured meeting transcripts and extracting key entities (names, dates, action items) to populate CRM records.
*   **Form Data Capture:** Parsing complex legal documents or application forms to reliably pull out specific fields like policy numbers or dates of service for downstream processing.