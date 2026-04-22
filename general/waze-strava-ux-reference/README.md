# WAZE STRAVA UX REFERENCE

> **Purpose:** Structured reference for the App Designer agent.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Waze + Strava UX Reference for DirtSync

**Purpose:** Structured reference for the App Designer agent. Every section maps a
proven pattern from Waze or Strava to the DirtSync off-road context.

**Last updated:** 2026-04-06

---

## 1. Navigation HUD (Active Turn-by-Turn)

### 1.1 Layout Zones

```
+------------------------------------------+
|  [TURN CARD — full width]                |  ← TOP (safe area inset + ~80pt)
|  ↰ Turn left on Main St          0.3 mi |
+------------------------------------------+
|                                          |
|                                          |
|            MAP (fills middle)            |  ← CENTER (all remaining space)
|              route line                  |
|          user arrow centered             |
|                                          |
+------------------------------------------+
|  SPEED    |    ETA BAR    |   REPORT     |  ← BOTTOM (~60-80pt)
|  [42 mph] | 12 min · 4.2mi| [▲ orange]  |
+------------------------------------------+
```

### 1.2 Turn Card (Top)

| Property | Waze Pattern | DirtSync Adaptation |
|----------|-------------|---------------------|
| Position | Pinned to top, full width | Same |
| Height | ~80pt (expands for complex turns) | Same |
| Background | Semi-transparent dark (#1A1A1A at 90% opacity) | Same |
| Turn icon | Left side, ~44pt, white arrow on colored circle | Same, add trail-fork icon variant |
| Distance to turn | Right-aligned, large bold text (~24pt) | Same |
| Street/trail name | Below turn icon, medium text (~16pt), truncated | Trail name instead of street |
| Next-after-next | Small secondary line below main instruction | Show next fork/intersection |
| Font weight | Distance = Bold 700, name = Regular 400 | Same |
| Text color | Primary white #FFFFFF, secondary #B0B0B0 | Same |

**Waze behavior:** Turn card compresses when far from turn (shows just icon + distance).
Expands with street name when within ~500m. Becomes urgent (larger arrow, voice prompt)
within 

*[truncated — see source for full prompt]*