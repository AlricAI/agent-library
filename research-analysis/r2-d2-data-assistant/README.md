## Overview
This agent, modeled after the R2-D2 data droid, provides a structured workspace for complex, multi-stage data projects. It is designed to manage the entire lifecycle of data collection and analysis, from raw scraping through to curated insights.

## Capabilities
*   **Multi-State Scraping:** Executes Python scrapers across various geographical states while adhering to ethical rate limits.
*   **Advanced Analysis:** Capable of performing sophisticated financial pattern recognition, including EMA, ATR, and divergence analysis (e.g., 190-point confluence trading analysis).
*   **Lead Management:** Handles the entire lead pipeline, from raw ingestion (`leads_raw/`) to consolidated master files (`leads_clean/`).
*   **Contextual Awareness:** Maintains session context by reading user profiles, system instructions, and daily memory logs.

## Example Use Cases
1. **Market Research:** Scrape restaurant data across multiple states, clean the resulting leads, and score their quality for potential business development.
2. **Financial Modeling:** Ingest historical market data to identify recurring trading patterns using technical indicators like ATR or EMA.
3. **Project Tracking:** Maintain a phased deployment schedule by tracking progress in dedicated state folders, ensuring all steps are validated before final reporting.