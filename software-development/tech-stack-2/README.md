# TECH STACK

> Current, codebase-accurate technology stack for the Flutter + Flame project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Nyxis — Tech Stack

Current, codebase-accurate technology stack for the Flutter + Flame project.

---

## Core Runtime

| Technology | Version | Purpose |
|------------|---------|---------|
| `Dart` | `^3.9.0` | Language/runtime |
| `Flutter` | SDK | Cross-platform app framework |
| `flame` | `^1.18.0` | Main game engine |
| `flame_audio` | `^2.10.0` | Sound playback |
| `flame_tiled` | `^1.20.0` | Tiled-map interoperability |

---

## Data, Models, and Serialization

| Package | Version | Usage |
|---------|---------|-------|
| `hive` | `^2.2.3` | Local persistence backend |
| `hive_flutter` | `^1.1.0` | Flutter integration for Hive |
| `freezed_annotation` | `^2.4.0` | Immutable model annotations |
| `json_annotation` | `^4.9.0` | JSON model annotations |
| `collection` | `^1.18.0` | Collection helpers |
| `equatable` | `^2.0.5` | Value equality utilities |
| `uuid` | `^4.0.0` | ID generation |

Build-time tooling:

| Package | Version | Usage |
|---------|---------|-------|
| `build_runner` | `^2.4.0` | Code generation runner |
| `freezed` | `^2.5.0` | Freezed code generation |
| `json_serializable` | `^6.8.0` | JSON serializer generation |
| `hive_generator` | `^2.0.1` | Hive adapter generation |

---

## Gameplay Systems and Patterns

- **Turn-based orchestration** via `TurnSystem`, `CombatSystem`, `MonsterBehaviorSystem`.
- **Event-driven integration** via `EventBus` and typed game events in `lib/core/`.
- **Registry-driven content** using `MonsterRegistry`, `ItemRegistry`, `LocationRegistry`, and `PortalRegistry`.
- **World flow architecture** uses `GameWrapper` as the canonical `GameState` owner for location gameplay, surface exits, and world map transitions.
- **Procedural generation pipeline** in `lib/services/generation/` with composable steps and generator registry routing.
- **Surface tile visuals** for overworld-entry locations are derived from `WorldMap` terrain and threaded through `FloorManager` into `SurfaceGenerator`.

---

## Active Project Lay

*[truncated — see source for full prompt]*