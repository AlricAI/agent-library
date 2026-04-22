# Prompt

> Build a new pipeline for **Istanbul Public Transit — Ridership Patterns & Metro Expansion Impact**.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Build a new pipeline for **Istanbul Public Transit — Ridership Patterns & Metro Expansion Impact**.

**Context:** Utilize Bruin MCP and Bruin CLI, reference Bruin docs. Follow @AGENTS.md strictly — these are the rules for this repo. If you are about to break any rule in AGENTS.md, stop and ask for clarification and permission before proceeding.

### Data source

All data comes from the Istanbul Metropolitan Municipality (IBB) Open Data Portal: https://data.ibb.gov.tr/en/
No API keys or authentication required for CSV downloads. All data is under the Istanbul Metropolitan Municipality Open Data License (permissive for analysis).

**1. Hourly Public Transport Data (Istanbulkart tap data)**
- URL: https://data.ibb.gov.tr/en/dataset/hourly-public-transport-data-set
- Publisher: BELBIM Inc. (Istanbulkart operator)
- Format: 60 monthly CSV files, ~1–1.8 GB each (~60 GB total uncompressed)
- Time range: January 2020 – December 2024
- Fields: `transition_date`, `transition_hour`, `transport_type_id`, `road_type`, `line`, `transfer_type`, `number_of_passage`, `number_of_passenger`, `product_kind`, `transaction_type_desc`, `town`, `line_name`, `station_poi_desc_cd`
- Coverage: all modes — IETT bus, metro, metrobus, Marmaray, IDO ferries, maritime services
- Includes: transfer vs direct trips, fare type (full/discounted), district, line name, station
- This is the core dataset. Due to size (~60 GB), process month-by-month in the Python asset and load incrementally.

**2. Rail Station-Level Ridership (with coordinates)**
- URL: https://data.ibb.gov.tr/en/dataset/rayli-sistemler-istasyon-bazli-yolcu-ve-yolculuk-sayilari
- Format: CSV (annual files, 11–101 MB per year)
- Time range: 2021–2025
- Fields: `passage_cnt`, `passanger_cnt`, `transaction_year`, `transaction_month`, `transaction_day`, `line`, `station_name`, `station_number`, `town`, `longitude`, `latitude`
- Daily station-level ridership with geographic coordinates — enables spatial analysis and mapping.

**3. Rail Rider

*[truncated — see source for full prompt]*