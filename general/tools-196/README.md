# TOOLS

> Reference commands, source URLs, and file schemas.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — Changelog Expert

Reference commands, source URLs, and file schemas. Load on demand.

---

## Watch List — Exact Fetch Commands

### 1. Claude Code
```bash
curl -sSL "https://raw.githubusercontent.com/anthropics/claude-code/main/CHANGELOG.md" | head -200
```
Parse for headers like `## X.Y.Z` or `## [X.Y.Z]`.

### 2. MapLibre iOS
GitHub releases API. The iOS repo was consolidated into the unified `maplibre-native` monorepo in 2024 — the old `maplibre-gl-native-ios` URL now 404s. Always use the unified repo:
```bash
curl -sSL -H "Accept: application/vnd.github+json" \
  "https://api.github.com/repos/maplibre/maplibre-native/releases?per_page=20"
```
Filter releases by tag prefix `ios-` since the monorepo tags all platforms (ios-, android-, gl-js-, etc.). Example tags: `ios-v6.5.0`, `ios-v6.6.0`. Parse: `.[] | select(.tag_name | startswith("ios-")) | .tag_name, .body`.

**If this URL also returns 404 in the future**, fall back to the GitHub web URL `https://github.com/maplibre/maplibre-native/releases` via WebFetch. Do NOT fabricate a version if the source cannot be reached — file a meta-issue instead (see HEARTBEAT step 2).

### 3. Ferrostar
```bash
curl -sSL -H "Accept: application/vnd.github+json" \
  "https://api.github.com/repos/stadiamaps/ferrostar/releases?per_page=10"
```

### 4. Valhalla
```bash
curl -sSL -H "Accept: application/vnd.github+json" \
  "https://api.github.com/repos/valhalla/valhalla/releases?per_page=10"
```

### 5. Swift
```bash
curl -sSL "https://raw.githubusercontent.com/apple/swift/main/CHANGELOG.md" | head -500
```

### 6. Supabase JS SDK
```bash
curl -sSL -H "Accept: application/vnd.github+json" \
  "https://api.github.com/repos/supabase/supabase-js/releases?per_page=10"
```

### 7. Anthropic SDK (Python + TypeScript)
```bash
curl -sSL -H "Accept: application/vnd.github+json" \
  "https://api.github.com/repos/anthropics/anthropic-sdk-python/releases?per_page=10"

curl -sSL -H "Accept: application/vnd.github+json" \
  "https://a

*[truncated — see source for full prompt]*