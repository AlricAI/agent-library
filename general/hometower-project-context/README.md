# Hometower project context

> Complete product decisions, tech stack, and requirements for the Hometower homelab inventory tool

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Hometower is a self-hosted homelab inventory management tool — Cloudcraft for homelabbers. Users draw infrastructure on a drag-and-drop canvas; the diagram is the inventory.

**Why:** Existing tools (diagramming apps) are flat and give no real inventory. Hometower bridges the gap.

**Phase 2 name:** LightTower (small teams, different branding)

## Final Tech Stack

- UI: NiceGUI
- Topology canvas: Cytoscape.js (embedded in NiceGUI)
- Map view: Leaflet.js + OpenStreetMap (embedded in NiceGUI)
- API: FastAPI + Pydantic (unified with NiceGUI via `ui.run_with()`)
- ORM: SQLModel + Alembic
- Database: PostgreSQL 16
- Auth: passlib (bcrypt) + python-jose (JWT)
- Logging: Loguru
- Deployment: Docker Compose (no reverse proxy in v1)

**Why FastAPI over Falcon:** NiceGUI runs FastAPI internally. Unifying them removes dual-server complexity and gives Pydantic validation + auto OpenAPI docs for free.

**Why Cytoscape.js over draw.io:** Data model IS the diagram — no XML parsing or dual representation. Network topology purpose-built library.

**Why Leaflet.js:** Open source, no API key, OpenStreetMap tiles, perfect for self-hosted.

## Product Decisions

| Decision | Choice | Reason |
|---|---|---|
| Concurrency | Last-write-wins | Simple, sufficient for solo/small team |
| Reverse proxy | None for v1 | Added complexity without clear benefit yet |
| First admin | .env vars (ADMIN_EMAIL, ADMIN_PASSWORD) | Simple, standard pattern |
| Custom fields | Yes — free key-value pairs per device | Power users need serial numbers, warranty dates etc |
| Location grouping | Yes — rack and geo types | Supports both physical racks and distributed infra |
| Map view | Yes — Leaflet.js + OpenStreetMap | Users have VPS, colocation, remote nodes |

## Features Confirmed for v1

- Drag-and-drop topology canvas (Cytoscape.js)
- Geographic map view (Leaflet.js)
- Device types: Server, Switch, Router, NAS, UPS, SBC, Workstation, VM, LXC, Docker Container, Application, VLAN, Subnet
- Connection types

*[truncated — see source for full prompt]*