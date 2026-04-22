# Prompt

> Build a new pipeline for **US Public Transit — COVID Recovery & Spending Efficiency**.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Build a new pipeline for **US Public Transit — COVID Recovery & Spending Efficiency**.

**Context:** Utilize Bruin MCP and Bruin CLI, reference Bruin docs. Follow @AGENTS.md strictly — these are the rules for this repo. If you are about to break any rule in AGENTS.md, stop and ask for clarification and permission before proceeding.

### Data source

This pipeline uses bulk CSV downloads (not APIs) from the US National Transit Database and the US Census Bureau.

**1. US National Transit Database (NTD) — Federal Transit Administration**
- Download page: https://www.transit.dot.gov/ntd/ntd-data
- Key files to download:
  - **Monthly Module (Adjusted Data Release)**: https://www.transit.dot.gov/ntd/data-product/monthly-module-adjusted-data-release — monthly ridership (UPT) and vehicle revenue miles (VRM) by agency and mode. CSV. ~900 agencies, 2002–present.
  - **TS1.1 Total Ridership Time Series**: https://www.transit.dot.gov/ntd/data-product/ts11-total-ridership-time-series — pre-aggregated national ridership totals by mode and month.
  - **Annual Database — Service**: https://www.transit.dot.gov/ntd/data-product/2022-annual-database-service — annual operational data: ridership, vehicle revenue hours/miles, route miles, stations. CSV.
  - **Annual Database — Operating Expenses**: https://www.transit.dot.gov/ntd/data-product/2022-annual-database-operating-expenses — operating expenses by agency and mode. CSV.
  - **Annual Database — Capital Expenses**: capital spending by agency. CSV.
  - **Agency Information**: https://www.transit.dot.gov/ntd/data-product/2022-annual-database-agency-information — agency metadata: name, city, state, UZA (urbanized area), service area population, service area sq miles. CSV.
- All files are free, public domain, no authentication required.
- Metric: "Unlinked Passenger Trips" (UPT) — each boarding counts as one trip. A ride with a transfer = 2 UPTs. This is the standard US transit ridership metric.
- NTD mode codes: `HR` (heavy rail/subwa

*[truncated — see source for full prompt]*