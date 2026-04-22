# TOOLS

> ## Domain References

### MapLibre Style Spec (Primary Reference)
- **Full spec:** https://maplibre.org/maplibre-style-spec/
- **Layers:** https://map

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — DirtSync MapLibre Style Expert

## Domain References

### MapLibre Style Spec (Primary Reference)
- **Full spec:** https://maplibre.org/maplibre-style-spec/
- **Layers:** https://maplibre.org/maplibre-style-spec/layers/
- **Sources:** https://maplibre.org/maplibre-style-spec/sources/
- **Glyphs:** https://maplibre.org/maplibre-style-spec/glyphs/
- **Sprite:** https://maplibre.org/maplibre-style-spec/sprite/
- **Expressions:** https://maplibre.org/maplibre-style-spec/expressions/

### MapLibre Native iOS API
- **GitHub:** https://github.com/maplibre/maplibre-native
- **iOS docs:** https://maplibre.org/maplibre-native/ios/api/

---

## Glyph PBF Inspection

Glyph files are binary Protocol Buffer files. You can inspect them with the `maplibre-gl-inspect` CLI or decode manually.

### Check which glyph ranges exist in the bundle
```bash
ssh dirtsyncmini@100.125.184.57 \
  'find /Users/dirtsyncmini/DirtSync/DirtSync/DirtSyncApp/Resources/glyphs -name "*.pbf" | sort'
```
Expected output (contiguous 256-char ranges):
```
.../glyphs/Open Sans Regular/0-255.pbf
.../glyphs/Open Sans Regular/256-511.pbf
.../glyphs/Open Sans Regular/512-767.pbf
.../glyphs/Open Sans Bold/0-255.pbf
.../glyphs/Open Sans Bold/256-511.pbf
```
**Red flag:** any gap in the range sequence (e.g. `0-255.pbf` exists but `256-511.pbf` is missing). MapLibre silently falls back for missing ranges — no error, just tofu characters.

### Decode a PBF glyph range (see what characters it covers)
```bash
# Install pbf decoder if needed
pip3 install mapbox-vector-tile 2>/dev/null || true

# Or use xxd to inspect the header (look for font name + range)
xxd /path/to/0-255.pbf | head -20
```

### Verify glyph path in style JSON matches actual directory structure
```bash
# Extract the glyphs field from style JSON
python3 -c "
import json
with open('style-dark-matter.json') as f:
    s = json.load(f)
print('glyphs:', s.get('glyphs', 'NOT SET'))
print('sprite:', s.get('sprite', 'NOT SET'))
"
```
The `{fontsta

*[truncated — see source for full prompt]*