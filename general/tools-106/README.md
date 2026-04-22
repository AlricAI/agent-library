# TOOLS

> You inherit all Feature Builder tools.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — DirtSync Offline Routing Engineer

You inherit all Feature Builder tools.
Full reference: `../feature-builder/TOOLS.md`

---

## Specialist Tools

### Ferrostar RouteStep Patch (MANDATORY on Mini)

Every `RouteStep` initializer on Mini requires two nil arguments that newer Ferrostar versions make optional. Without these the build fails silently on the Mini's version.

```swift
// CORRECT — Mini-compatible
RouteStep(
    geometry: coordinates,
    distance: distance,
    duration: duration,
    roadName: roadName,
    instruction: instruction,
    visualInstructions: [],
    utterances: [],
    drivingSide: nil,                // REQUIRED on Mini
    roundaboutExitNumber: nil        // REQUIRED on Mini
)

// WRONG — compiles on laptop, breaks on Mini
RouteStep(
    geometry: coordinates,
    distance: distance,
    duration: duration,
    roadName: roadName,
    instruction: instruction,
    visualInstructions: [],
    utterances: []
    // Missing drivingSide + roundaboutExitNumber → Mini build failure
)
```

Apply this patch immediately after fetching code on Mini. Check it on every build.

---

### Valhalla Costing JSON Schemas

#### Primary — Motorcycle (trail riding)
```json
{
  "locations": [
    {"lon": -81.3140, "lat": 37.6628, "type": "break"},
    {"lon": -81.3180, "lat": 37.6650, "type": "break"}
  ],
  "costing": "motorcycle",
  "costing_options": {
    "motorcycle": {
      "use_trails": 1.0,
      "use_tracks": 1.0,
      "use_highways": 0.0,
      "service_penalty": 500,
      "service_factor": 5.0,
      "use_living_streets": 0.0
    }
  },
  "directions_options": {
    "units": "miles"
  },
  "alternates": 2
}
```

**CRITICAL:** `use_trails` MUST be `1.0`. The default is `0.0`, which causes routes to use roads exclusively. Verify in raw JSON before every request.

#### Fallback — Auto (road segment when trail unavailable)
```json
{
  "locations": [...],
  "costing": "auto",
  "costing_options": {
    "auto": {
      "use_highways": 0.3,


*[truncated — see source for full prompt]*