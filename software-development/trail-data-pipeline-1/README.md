# Trail Data Pipeline

> > Last updated: April 2, 2026
> Used by: DirtSync engineers, data pipeline agents, trail import agents
> Origin: Sessions 64-71 — trail data architect

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Trail Data Pipeline Specialist

> Last updated: April 2, 2026
> Used by: DirtSync engineers, data pipeline agents, trail import agents
> Origin: Sessions 64-71 — trail data architecture and field testing

---

## Goal
Manage DirtSync's trail data from source to rendering. Understand the pipeline: Supabase → GeoJSON → MBTiles → MapLibre rendering → trail detection.

## Data Pipeline

### Source of Truth
- **Supabase table:** `trail_lines` (columns: trail_name, difficulty, trail_system, coordinates (JSONB), distance_miles, is_outlaw, etc.)
- **Gold-verified systems:** Burning Rock (96 trails, 67+29 outlaw) and Kidds Dairy Farm (11 trails)

### Pipeline Flow
```
Supabase trail_lines → export → all-trails.geojson → tippecanoe → trails.mbtiles → bundled in app
```

### Key Files
| File | Purpose | Size |
|------|---------|------|
| `DirtSync/tiles/all-trails.geojson` | Source GeoJSON for MBTiles | ~5MB |
| `DirtSync/DirtSyncApp/Resources/trails.mbtiles` | Bundled vector tiles | ~5MB |
| `valhalla_tiles.tar` | Routing graph tiles | varies |

### MBTiles Specifications
- **Zoom range:** z8-z16 (MapLibre overzooms beyond z16)
- **Layer name:** `trails` (from tippecanoe `-l trails`)
- **Build command:** `tippecanoe -o trails.mbtiles -z 16 -Z 8 --force --no-feature-limit --no-tile-size-limit -l trails all-trails.geojson`
- **Properties:** name, system, difficulty, distance_miles, is_connector, is_outlaw, ref, route_type

## Trail Detection Architecture (Session 71 — CORRECT approach)

### Primary: In-Memory GeoJSON Nearest-Point-on-Line
1. Trail data loaded at app launch: `TrailDataService.shared.trails` (1112 features)
2. Each GPS update → bounding box pre-filter (skip trails >200m away)
3. For each candidate → iterate every line segment → project GPS onto segment → clamp t∈[0,1]
4. Minimum distance < 100m = "on trail"
5. Extract: trail name, difficulty, system from TrailFeature.properties

### Nearest-Point-on-Segment Math
```swift
func nearestPointOnSegment(point,

*[truncated — see source for full prompt]*