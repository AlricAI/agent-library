## Overview
This agent acts as a dedicated Messaging Architect for B2B technology consulting firms. Its primary function is to take disparate raw data—such as CRM exports, lead forms, and market signals—and systematically process it through three core stages: Parsing, Finding Patterns, and Interpretation.
The goal is to move beyond simple data aggregation to build actionable, evidence-based outbound messaging frameworks that resonate with specific prospect needs.

## Capabilities
* **Data Parsing:** Extracts structured fields (Status, Industry, Company Size) from various sources like CSVs and CRM exports, using descriptive text as a fallback for missing data.
* **Pattern Identification:** Uses regex and keyword analysis to categorize stated needs (e.g., SharePoint migration, Power BI), infer company types from domains (.gov, .edu), and map job titles to functional roles and seniority levels.
* **Cross-Tabulation & Interpretation:** Cross-references multiple extracted data points (Company Type $\times$ Ask, Title $\times$ Service) to quantify demand. It then maps these needs directly to the consulting firm's service catalog and identifies underlying financial levers (cost reduction, revenue increase).
* **Output Generation:** Produces plain-English, jargon-free messaging outputs optimized for scannability.

## Example Use Cases
1. **Opportunity Qualification:** Given a list of 50 leads with varied notes, the agent can parse them to determine that 60% are interested in 'Data Analytics' and primarily belong to the 'Healthcare' sector, allowing sales to focus messaging immediately.
2. **Campaign Refinement:** After an inbound marketing campaign, the agent analyzes form submissions to identify if the primary interest is related to 'Cloud Migration' or 'CRM implementation,' refining follow-up content accordingly.
3. **Market Signal Analysis:** When provided with industry reports, it can cross-reference stated pain points against service offerings to build a comprehensive narrative demonstrating immediate value proposition.