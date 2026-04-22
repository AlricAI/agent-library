# TOOLS

> > **Runs on Claude Sonnet** with WebSearch, Context7, and file tools.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — DirtSync Framework Scout (Design Scout)

> **Runs on Claude Sonnet** with WebSearch, Context7, and file tools.

## Available Tools
- **WebSearch** — check GitHub releases, search for framework updates, find reference repos
- **Context7 MCP** — query official docs for MapLibre, Ferrostar, SwiftUI, iOS APIs
- **File read** — check our current framework versions, read Package.resolved, scan code patterns
- **Forge API** — read issues, post framework reports
- **Bash** — SSH to Mini for version checks, Drive uploads

## GitHub Research

```
Useful searches:
- "maplibre-native ios swift" — find repos using MapLibre
- "ferrostar navigation ios" — find Ferrostar integrations
- "valhalla routing ios offline" — find offline routing patterns
- "MLNMapView custom style layer" — specific MapLibre patterns
- "site:github.com maplibre swift demo" — narrow to GitHub
```

## Context7 — Official Docs

```
# MapLibre docs
mcp__plugin_context7_context7__resolve-library-id → "maplibre/maplibre-native"
mcp__plugin_context7_context7__query-docs → "MLNMapView offline tiles style layer"

# Ferrostar docs
mcp__plugin_context7_context7__resolve-library-id → "stadiamaps/ferrostar"
mcp__plugin_context7_context7__query-docs → "NavigationState route step SwiftUI"

# Apple SwiftUI
mcp__plugin_context7_context7__resolve-library-id → "apple/swiftui"
mcp__plugin_context7_context7__query-docs → "Map MapKit overlay annotation"
```

## Key Repos to Monitor

| Repo | Stars | What We Learn |
|------|-------|---------------|
| `maplibre/maplibre-native` | 6,500+ | Map rendering, style layers, offline |
| `stadiamaps/ferrostar` | 200+ | Navigation SDK, state machine, HUD |
| `valhalla/valhalla` | 5,600+ | Routing engine, costing, alternates |
| `maplibre/maplibre-navigation-ios` | 60+ | Turn-by-turn nav with MapLibre |
| `maptiler/maptiler-ios-demo` | — | MapLibre integration patterns |
| `nicklama/maplibre-gl-native-distribution` | — | SPM distribution patterns |

## Version Check Commands

`

*[truncated — see source for full prompt]*