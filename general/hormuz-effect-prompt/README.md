# Hormuz Effect Prompt

> Build a new pipeline similar to @stackoverflow-trends for **global energy crisis tracking — oil, gas, and commodity price shocks driven by the 2026 Strait of Hormuz crisis**.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Pipeline Prompt: The Hormuz Effect

Build a new pipeline similar to @stackoverflow-trends for **global energy crisis tracking — oil, gas, and commodity price shocks driven by the 2026 Strait of Hormuz crisis**.

**Context:** utilize Bruin MCP and Bruin CLI, reference Bruin docs. Follow @AGENTS.md strictly — these are the rules for this repo. If you are about to break any rule in AGENTS.md, stop and ask for clarification and permission before proceeding.

### Data source

**FRED API** (free, key required — already configured or register at https://fred.stlouisfed.org/docs/api/api_key.html):
- Base URL: `https://api.stlouisfed.org/fred/series/observations`
- Key series to ingest:
  - `DCOILBRENTEU` — Brent crude oil price (daily, USD/barrel, 1987–present)
  - `DCOILWTICO` — WTI crude oil price (daily, USD/barrel, 1986–present)
  - `GASREGW` — US regular gasoline price (weekly, USD/gallon)
  - `DHHNGSP` — Henry Hub natural gas spot price (daily, USD/MMBtu)
  - `GOLDAMGBD228NLBM` — Gold price London fixing (daily, USD/troy oz)
  - `PWHEAMTUSDM` — Global wheat price (monthly, USD/metric ton)
  - `PCOPPUSDM` — Global copper price (monthly, USD/metric ton)
- Auth: API key passed as `&api_key=KEY` query parameter
- Response format: JSON with `&file_type=json`
- Pagination: use `observation_start` and `observation_end` params for date range

All series can be fetched from the same endpoint, just varying the `series_id` param.

### What to extract

- **Daily prices** for oil (Brent + WTI), natural gas, and gold — going back to 1987 for oil, as far as available for others
- **Weekly US gasoline prices** — going back to 1990
- **Monthly commodity prices** (wheat, copper) — going back to 2000
- All prices in USD, with date as the primary key per series

### Naming

All asset/table names should have prefix **`hormuz_`**
Destination: BigQuery

### Dashboard questions

The goal is a final Streamlit + Altair dashboard that answers:

1. **"How does the 2026 Hormuz crisis compare to

*[truncated — see source for full prompt]*