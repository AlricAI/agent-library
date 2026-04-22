# Ferrostar Nav

> > Last updated: April 2, 2026
> Used by: DirtSync engineers, navigation agents
> Origin: Sessions 63-71 — navigation implementation and field testing


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Ferrostar Navigation Specialist

> Last updated: April 2, 2026
> Used by: DirtSync engineers, navigation agents
> Origin: Sessions 63-71 — navigation implementation and field testing

---

## Goal
Build Ferrostar-based turn-by-turn navigation features for the DirtSync trail riding app.

## DirtSync Ferrostar Setup
- **Package:** `stadiamaps/ferrostar` (Swift, via SPM)
- **Location provider:** ALWAYS use `CoreLocationProvider` (feeds both MapLibre AND Ferrostar)
- **Route source:** Valhalla routes converted via `convertToFerrostarRoute()`
- **Voice:** Ferrostar handles voice during navigation. TrailNavigationState voice is fallback only.

## Critical Rules

### GPS Provider: CoreLocationProvider ONLY
- `CoreLocationProvider` reads from `CLLocationManager` which gets real GPS (device) or simctl (simulator)
- `SimulatedLocationProvider` feeds Ferrostar INTERNALLY only — MapLibre's map view does NOT receive these updates
- Using SimulatedLocationProvider creates dual GPS streams that diverge → nav exits immediately
- For simulator testing: use `simctl location start` with waypoints → feeds CLLocationManager → drives BOTH map AND Ferrostar

### Voice Navigation
- Ferrostar has its own `AVSpeechSynthesizer`
- TrailNavigationState has its own `AVSpeechSynthesizer`  
- JunctionDetectionService has its own voice manager
- **3 synthesizers can overlap!** Only Ferrostar speaks during active navigation.
- Set `trailNavState.voiceManager.isNavigationActive = true` when Ferrostar starts

### Dark Theme
- Navigation uses CARTO Dark Matter basemap
- `mapStyleManager.useNavDarkTheme = true` when nav starts
- `mapStyleManager.useNavDarkTheme = false` when nav stops
- Free riding also uses dark theme via `useFreeRiderDarkTheme`

### Camera During Navigation
- `.followWithCourse` mode — map rotates to direction of travel (GPS course, not compass)
- z18 zoom, pitch 45°
- Pan cooldown: 5 seconds after user pan, then auto-recenter
- State machine controls camera: approaching→onRo

*[truncated — see source for full prompt]*