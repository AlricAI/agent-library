# Prompt

> ---

## Prompt

Build a new pipeline for **Hong Kong Public Transport Network**.

**Context:** Utilize Bruin MCP and Bruin CLI, reference Bruin docs. 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Pipeline Build Prompt

---

## Prompt

Build a new pipeline for **Hong Kong Public Transport Network**.

**Context:** Utilize Bruin MCP and Bruin CLI, reference Bruin docs. Follow @AGENTS.md strictly — these are the rules for this repo. If you are about to break any rule in AGENTS.md, stop and ask for clarification and permission before proceeding.

### Data source

There are three data sources covering Hong Kong's public transport system:

**1. Static GTFS Feed (data.gov.hk)**

- Source: Hong Kong government open data portal (`data.gov.hk`)
- Format: ZIP archive containing CSV/text files (`routes.txt`, `stops.txt`, `trips.txt`, `stop_times.txt`, `calendar.txt`)
- Coverage: KMB buses, CTB/NWFB Citybus, trams, ferries
- Note: `stop_times.txt` exceeds 100 MB — handle large file ingestion appropriately
- Refresh: full refresh daily (WRITE_TRUNCATE)

**2. MTR Open Data Portal (opendata.mtr.com.hk)**

- Four CSV datasets:
  - `mtr_lines_stations` — heavy rail line and station data
  - `mtr_bus_stops` — MTR feeder bus routes and stops
  - `mtr_fares` — station-to-station fare table
  - `mtr_light_rail_stops` — Light Rail routes and stops
- **Important:** Requests require a `User-Agent` header (e.g. `"Mozilla/5.0"`) or the connection will be dropped
- **Important:** CSVs have UTF-8 BOM — decode with `utf-8-sig` to avoid character corruption

**3. MTR Real-Time Schedule API (rt.data.gov.hk)**

- Real-time train arrival/departure predictions
- JSON format with line, station, and timestamp fields
- Poll every minute for streaming ingestion

Note: MTR does not publish GTFS data. Trip-level data for the heavy rail network is not publicly available — this limits headway and crowding analysis for MTR lines.

Credentials are in @.bruin.yml

### What to extract

- **Stops:** stop ID, name, latitude, longitude — for all bus, tram, ferry, and MTR stops
- **Routes:** route ID, name, type (bus/tram/ferry), operator
- **Trips:** trip ID, route association, service calendar (weekday/we

*[truncated — see source for full prompt]*