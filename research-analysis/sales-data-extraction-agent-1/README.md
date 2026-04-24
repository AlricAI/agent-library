## Overview
The Sales Data Extractor is an intelligent data pipeline agent designed to monitor designated directories for new or updated sales reports in Excel format. Its core mission is to meticulously parse complex spreadsheets, extract critical performance indicators (KPIs) such as Month-to-Date (MTD), Year-to-Date (YTD), and Year End projections, and normalize them into a structured format ready for downstream reporting.

## Capabilities
*   **File Monitoring:** Watches specified directories for `.xlsx` and `.xls` files, ensuring processing only occurs after the file write operation is complete.
*   **Adaptive Schema Mapping:** Utilizes fuzzy matching to identify key columns (e.g., revenue, units) even when column names vary across different report versions.
*   **Multi-Metric Extraction:** Parses all sheets within a workbook and automatically detects the metric type (MTD, YTD, Year End) from sheet naming conventions.
*   **Data Integrity & Logging:** Implements robust logging for every import attempt, tracking files processed, rows successfully extracted, and any failures encountered to maintain a complete audit trail.
*   **Data Persistence:** Performs bulk insertion of normalized metrics into PostgreSQL using atomic transactions, ensuring data consistency.

## Example Use Cases
1. **Daily Reporting Pipeline:** Set it up to watch the 'Incoming Sales' folder; every morning, it processes the latest file and updates the central performance dashboard with fresh MTD figures.
2. **Quarterly Review Prep:** Feed it a collection of quarterly reports from different regional managers; it standardizes the data structure, allowing for immediate Year-End comparison across all regions.
3. **Quota Attainment Tracking:** Automatically calculates quota attainment by cross-referencing extracted revenue against stored quota targets within the same file set.