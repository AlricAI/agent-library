# TOOLS

> ## Available Tools
- File read/write/edit (implementation plans, architecture docs)
- Glob/Grep (codebase exploration, dependency mapping)
- Bash (git

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — DirtSync Solutions Architect

## Available Tools
- File read/write/edit (implementation plans, architecture docs)
- Glob/Grep (codebase exploration, dependency mapping)
- Bash (git status, swift package resolve, file counts)

## Architecture Diagrams
- **Excalidraw MCP** — create architecture diagrams, data flow charts, dependency maps
  - Use for: system architecture, component dependency diagrams, data flow
- **Context7 MCP** — query official framework docs
  - Ferrostar navigation: `resolve-library-id` → "stadiamaps/ferrostar"
  - MapLibre: `resolve-library-id` → "maplibre/maplibre-gl-native"
  - Valhalla: query routing engine docs

## Codebase Exploration

```bash
# Count files by type
find ~/DirtSync/DirtSync -name "*.swift" | wc -l

# Find all services
find ~/DirtSync/DirtSync -path "*/Services/*.swift" | sort

# Search for usage of a service
grep -r "NavigationService.shared" ~/DirtSync/DirtSync --include="*.swift" -l

# Check imports (dependency map)
grep -r "^import" ~/DirtSync/DirtSync/Services/NavigationService.swift
```

## Technology Stack Reference

```
iOS:        Swift 6, SwiftUI, MVVM
Maps:       MapLibre GL Native iOS v6.x — MLNMapView, custom styles, annotations
Navigation: Ferrostar — NavigationState, RouteAdapter, custom HUD views
Routing:    Valhalla on Fly.io (trail tiles only) + HybridRoutingService (roads)
Backend:    Supabase (lldipxvwocpqncixlnxj) — Auth, Realtime, Storage, Postgres
Offline:    MBTiles (map tiles), bundled GeoJSON (trail data), SQLite (local state)
Testing:    XCTest (unit), XCUITest (UI), iOS Simulator (iPhone 16)
```

## Project File Structure
```
DirtSync/
├── DirtSync.xcodeproj
├── DirtSync/
│   ├── DirtSyncApp.swift
│   ├── Views/
│   │   ├── Navigation/NavigationHUDView.swift
│   │   ├── Navigation/RoutePreviewView.swift
│   │   ├── Map/MapContainerView.swift
│   │   └── Rides/RideRecordingView.swift
│   ├── Services/
│   │   ├── NavigationService.swift           — nav state machine
│   │   ├── TrailDete

*[truncated — see source for full prompt]*