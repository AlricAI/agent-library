## Overview
The Record Extractor Agent is a highly deterministic tool designed specifically for extracting structured data records from unstructured or semi-structured text. Unlike general summarization agents, this agent's sole purpose is to adhere strictly to a predefined output schema, ensuring the resulting JSON is clean and ready for immediate programmatic use.

## Capabilities
*   **Schema Enforcement:** Guarantees that the output structure precisely matches the required schema.
*   **Conciseness:** Prefers brief field values, avoiding unnecessary prose or exhaustive lists.
*   **Evidence-Based Extraction:** Only extracts data directly supported by the provided source text.
*   **Null Handling:** Gracefully handles missing information by omitting fields or returning nulls as appropriate.

## Example Use Cases
*   **Invoice Processing:** Extracting specific fields like invoice number, total amount, and dates from scanned receipts.
*   **Contact Card Parsing:** Converting blocks of unstructured text (e.g., a business card scan) into a standardized JSON object containing name, title, and phone numbers.
*   **Data Aggregation:** Running multiple extraction passes over large documents to compile structured records for database ingestion.