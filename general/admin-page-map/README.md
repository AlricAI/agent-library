# ADMIN PAGE MAP

> **Full technical map:** CSS, UI, layout, functions, API calls, callbacks, components, state, and keyboard behavior.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VPN Suite Admin — https://vpn.vega.llc/admin

**Full technical map:** CSS, UI, layout, functions, API calls, callbacks, components, state, and keyboard behavior.

---

## 0. Live UI snapshot (Dashboard tab)

Captured from browser at `https://vpn.vega.llc/admin` (authenticated).

- **Top bar left:** Hamburger (☰), Shield + "AmneziaWG", Region dropdown ("All regions"), "Prod" badge.
- **Top bar center:** API ok, Prom ok, Nodes PROD 1/1 (green); Sessions 4; Error Live (80s auto) Updated 14s ago 0.00%; refresh; bell; search; theme (moon); Log out.
- **Main:** "Dashboard" title; buttons Servers, Audit, Telemetry, Resync, Refresh, settings. Cards: Cluster Health Matrix (table), Telemetry health (Fresh, Nodes 7 OK / 5 degraded / 0 down), Traffic & Load, Active Incidents (0).
- **Bottom nav (mobile):** OV Dashboard (active), SV Servers, TM Telemetry, US Users, ST Settings.

---

## 1. Entry point and configuration

### 1.1 Bootstrap

| Item | Value |
|------|--------|
| **Entry file** | `frontend/admin/src/main.tsx` |
| **Root element** | `document.getElementById("root")` |
| **Router** | `react-router-dom` `BrowserRouter` with `basename="/admin"` |
| **Base path** | `/admin` (overridable via `VITE_ADMIN_BASE` in .env) |

**Config module:** `frontend/admin/src/config.ts`  
- `ADMIN_BASE`: `import.meta.env.VITE_ADMIN_BASE` or `"/admin"`. Used for redirects (e.g. logout → `${ADMIN_BASE}/login`).

### 1.2 Provider tree (order)

1. `React.StrictMode`
2. `BrowserRouter` (basename `/admin`)
3. `QueryClientProvider` — `QueryClient` with:
   - `queries.retry: 1`
   - `queries.staleTime: 30000`
   - `queries.refetchOnWindowFocus: false`
4. `TelemetryProvider` (see §9)
5. `ThemeProvider` — `themes: ["dark", "dim", "light"]`, `defaultTheme: "dark"`, `storageKey: "vpn-suite-admin-theme"`
6. `App`

### 1.3 CSS loading order (main.tsx)

1. `@vpn-suite/shared/global.css`
2. `./tailwind.css`
3. `./admin.css`

### 1.4 API base URL

**Source:** `frontend/admin/src/shared/constants.ts` (`ge

*[truncated — see source for full prompt]*