# CLAUDE

> React 19 + TypeScript + Tailwind CSS 4 + Vite 7 custom panel for Home Assistant.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Home Assistant Custom Dashboard

React 19 + TypeScript + Tailwind CSS 4 + Vite 7 custom panel for Home Assistant.

## Commands

```bash
npm run dev           # Start dev server with HA proxy
npm run build         # TypeScript check + Vite build
npm run lint          # ESLint
npm run preview       # Preview production build
npx tsc -b --noEmit   # TypeScript check only (no build)
```

Deploy from project root: `make deploy-dashboard` (NOT raw rsync).

## Architecture

```
src/
  providers/HAProvider.tsx   # @hakit/core HassConnect wrapper (auth + WS)
  App.tsx                    # View registry → Shell
  views/                    # Top-level pages (Home, Climate, Energy, Security, Settings, SystemHealth)
  components/
    layout/                 # Shell, Header, BottomNav, Sidebar
    cards/                  # Data display cards (RoomCard, CameraCard, VacuumCard, etc.)
    controls/               # Interactive controls (LightControl, ClimateModePicker, ScheduleEditor, etc.)
    popups/                 # Modal dialogs (CameraPopup, RoomPopup, AcControlPopup, ZoneHistoryPopup)
    Go2RtcPlayer.tsx        # MSE player for desktop camera streams
    WebRtcPlayer.tsx        # WebRTC player for mobile camera streams
  hooks/                    # Custom hooks (useHistory, useSolarForecast, useWeatherForecast, etc.)
  lib/                      # Utilities (entities, areas, format, icons, camera-utils, snapshot-api)
                            # Control hooks: useControlCommit, useNumericControl, useSliderControl, useControlGroup
```

## Key Patterns

### Component Conventions
- **Naming**: `*View` (route pages), `*Card` (data display), `*Control` (interactive widgets), `*Popup` (modal dialogs)
- **Props**: `interface FooProps { ... }` (always `interface`, not `type`, for component props). Export prop interfaces when the component is reusable.
- **Exports**: Named exports for components (`export function FooCard`). Only `App.tsx` uses default export.
- **Import order**: Rea

*[truncated — see source for full prompt]*