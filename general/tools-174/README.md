# TOOLS

> > Reference for all tools, commands, schemas, and scripts this agent uses.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS — DirtSync Trail Data Engineer

> Reference for all tools, commands, schemas, and scripts this agent uses.

---

## Budget

| Target | Hard cap | Models allowed |
|--------|----------|----------------|
| $1.50/day | $4.00/day | Claude Sonnet, Codex (GPT-5.x), Gemini |

Use Sonnet or Codex for pipeline work. Opus only for architecture decisions (escalate to CEO).

---

## Tippecanoe

### Primary MBTiles Build Command

```bash
tippecanoe \
  -o DirtSync/DirtSyncApp/Resources/trails.mbtiles \
  -z 16 -Z 8 \
  --force \
  --no-feature-limit \
  --no-tile-size-limit \
  -l trails \
  DirtSync/tiles/all-trails.geojson
```

### Flag Reference

| Flag | Value | Why |
|------|-------|-----|
| `-z 16` | max zoom 16 | MapLibre overzooms beyond z16 — no benefit to higher |
| `-Z 8` | min zoom 8 | Trails not visible at country level |
| `--force` | (no value) | Overwrite existing output file |
| `--no-feature-limit` | (no value) | Don't drop trails due to tile density limits |
| `--no-tile-size-limit` | (no value) | Trails are complex polylines — don't truncate |
| `-l trails` | layer name | MapLibre style references this layer by name — must match |

### Smoke Test After Build

```bash
sqlite3 DirtSync/DirtSyncApp/Resources/trails.mbtiles \
  "SELECT zoom_level, COUNT(*) FROM tiles GROUP BY zoom_level ORDER BY zoom_level;"
```

Expected: rows at z8 through z16. If z16 is empty, the GeoJSON has no features.

```bash
ls -lh DirtSync/DirtSyncApp/Resources/trails.mbtiles
```

Expected: ≥ 1MB (real trail data). If < 100KB, the GeoJSON was empty or path was wrong.

---

## osmium-tool

### Extract Trail Area from OSM PBF

```bash
# Extract a bounding box from a regional OSM dump
osmium extract \
  --bbox -78.42,37.80,-78.35,37.84 \
  --output kidds-dairy-area.osm.pbf \
  virginia-latest.osm.pbf

# Filter to trail-related ways only
osmium tags-filter \
  kidds-dairy-area.osm.pbf \
  w/highway=path w/highway=track w/highway=cycleway w/route=mtb \
  --output kidds-dairy-trails.o

*[truncated — see source for full prompt]*