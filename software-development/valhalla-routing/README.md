# Valhalla Routing

> > Last updated: April 2, 2026
> Used by: DirtSync engineers, routing agents, navigation agents
> Origin: Session 71 — official Valhalla documentation 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Valhalla Routing Specialist

> Last updated: April 2, 2026
> Used by: DirtSync engineers, routing agents, navigation agents
> Origin: Session 71 — official Valhalla documentation research

---

## Goal
Build Valhalla-based routing features using documented APIs. The DirtSync app uses valhalla-mobile (Swift) with locally bundled tiles for offline trail routing.

## DirtSync Valhalla Setup
- **Package:** `Rallista/valhalla-mobile` v0.3.1 (latest: 0.5.0)
- **Tiles:** `valhalla_tiles.tar` bundled in app (177 tiles, Kidds Dairy area)
- **Config:** Created at runtime via `createValhallaConfig(tilesTarPath:)`
- **Instance:** Shared via `RoutingService.shared.valhalla` → `HybridRoutingService.shared.setValhalla()`
- **Costing:** Uses `auto` and `bicycle` profiles. `motorcycle` profile available but untested.

## Swift API (Current — v0.3.1)

The wrapper exposes ONLY `route`:
```swift
public func route(request: RouteRequest) throws -> RouteResponse  // typed
public func route(rawRequest: String) -> String                    // raw JSON
```

No `locate`, `trace_route`, `trace_attributes`, `matrix`, `isochrone`, or `status`.

### Raw JSON Routing
Use `route(rawRequest:)` for features not in the typed API:
- Alternates (typed RouteResponse drops them — must parse raw JSON)
- Custom costing options
- Exclude locations/polygons

## Valhalla C++ Actor Endpoints (available in C++, NOT in Swift wrapper)
| Endpoint | Purpose | In Swift? |
|----------|---------|-----------|
| `route` | A→B routing | ✅ Yes |
| `locate` | "What road/trail am I on?" | ❌ No — need fork |
| `trace_route` | Map match GPS trace to roads | ❌ No |
| `trace_attributes` | Detailed edge attributes along trace | ❌ No |
| `matrix` | Time/distance matrix | ❌ No |
| `isochrone` | Reachability polygons | ❌ No |
| `height` | Elevation profile | ❌ No |
| `status` | Server/tile health check | ❌ No |

### Adding `locate` (Future — 6 files, ~30 lines)
Fork `Rallista/valhalla-mobile`, add to:
1. `valhalla_actor.h` 

*[truncated — see source for full prompt]*