# poi-discovery-v2

> Discover POIs near a trail system — names and addresses only, NO coordinates. Separation of concerns: discovery finds businesses, geocoder pins them. Triggers on: discover POIs, find businesses near trails, POI research, what's near the trails, find restaurants gas lodging near trails.


## Model
- **Default:** `sonnet`

## System Prompt
## Goal

Find all businesses and points of interest near a DirtSync trail system. Output a structured list of business name, street address, category, phone, and hours. Do NOT attempt to get coordinates — the poi-geocoder skill handles that separately. This separation prevents the #1 failure mode: city-centroid coordinates that land 1-2mi off.

## Definition of Done
**YOU ARE NOT DONE UNTIL ALL OF THIS IS TRUE:**
1. ≥40 POIs found (for systems near towns >2,000 pop)
2. All 17 categories searched (see category list below)
3. ≥6 restaurants/food entries (search pizza, BBQ, diner, fast food, breakfast separately)
4. ≥1 emergency/medical entry (clinic in nearest town, NOT just distant hospital)
5. Every POI has a real street address (NOT "Sophia, WV" — need house number + street)
6. Results written to Supabase `trail_waypoints` with category and description containing address
7. Self-audit checklist completed — zero categories skipped

## Pre-Made Decisions
**DO NOT ask about these. They are already decided.**

| Decision | Answer |
|----------|--------|
| Coordinate source | DO NOT geocode. Leave lat/lng as trail system center. Geocoder skill fixes later. |
| Target table | `trail_waypoints` in DirtSync Supabase (`lldipxvwocpqncixlnxj`) |
| Radius cap | 10 miles from trail system center — hard limit |
| Category column | Use exact values: `fuel`, `restaurant`, `lodging`, `camping`, `gear_shop`, `emergency`, `grocery`, `liquor`, `tow_service`, `auto_parts`, `laundromat`, `car_wash`, `pharmacy`, `atm`, `attraction`, `trailhead`, `parking` |
| Naming | Actual business name. NOT listing descriptions like "Cozy 2BR cabin with WiFi" |
| Dedup | Check existing POIs in table before inserting — match on name + trail_system |

## Trail System Lookup

| System | Lat | Lon | Nearby Towns |
|--------|-----|-----|--------------|
| Burning Rock | 37.73 | -81.35 | Sophia, Beckley, Ghent |
| Rockhouse | 37.56 | -81.77 | Gilbert, Mingo County |
| (See poi-research.md for full table of 1

*[truncated — see source for full prompt]*