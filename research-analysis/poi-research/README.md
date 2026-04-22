# Poi Research

> ## Purpose

Research all points of interest (POIs) within a configurable radius of a DirtSync trail system. Collect business details (name, address, c

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: POI Research

## Purpose

Research all points of interest (POIs) within a configurable radius of a DirtSync trail system. Collect business details (name, address, coordinates, phone, hours, ratings, ATV-friendliness) and write structured results to a Google Sheet tab via the workspace-mcp CLI.

This skill runs once per trail system. DirtSync has 17 systems — each gets its own Google Sheet tab in a shared spreadsheet.

## When to Use

- When onboarding a new trail system and need POI data
- When refreshing stale POI data (quarterly recommended)
- Before a trail system launch (marketing/rider prep)
- When Steve asks "what's near [trail system]?"

## Pre-Task Context Loading

1. Load [[companies/dirtsync.md]] for DB schema + API reference
2. Use the trail system lookup table below (or coordinates from task description)
3. Check existing Google Sheet tabs for previously-researched data (dedup)

## Required Capabilities

- **Web search** — find businesses near GPS coordinates
- **Web fetch** — get business details (phone, hours, ratings, coordinates)
- **Bash** — run `workspace-mcp` CLI to write Google Sheets
- **Analysis** — dedup, Haversine distance calc, coordinate verification

## Input Parameters

| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| TRAIL_SYSTEM_NAME | Yes | — | e.g., "Burning Rock" |
| CENTER_LAT | No | Lookup table | Center latitude of the trail system |
| CENTER_LON | No | Lookup table | Center longitude of the trail system |
| RADIUS_MILES | No | 10 | Search radius in miles |
| GOOGLE_SHEET_ID | Yes | — | Spreadsheet ID to write to |
| DRIVE_FOLDER_ID | No | 18qQk2kQRHEb45ze_oxMNU_fzr_aiiLDh | DirtSync/POI Data/ folder |

## Trail System Lookup Table

Use these coordinates if CENTER_LAT/CENTER_LON are not provided. Nearby towns improve web search accuracy for rural areas.

| System | Lat | Lon | State | Nearby Towns |
|--------|-----|-----|-------|--------------|
| Bearwallow | 38.10 | -80.

*[truncated — see source for full prompt]*