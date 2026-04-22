---
name: TECH STACK
description: Current, codebase-accurate technology stack for the Flutter + Flame project.
model: claude-sonnet-4-5
---
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

## Active Project Layout

```
lib/
├── core/
├── config/
├── models/
│   ├── entities/
│   └── world/
├── game/
│   ├── nyxis_game.dart
│   ├── components/
│   ├── services/
│   └── systems/
├── services/
│   ├── audio_service.dart
│   ├── pathfinding_service.dart
│   ├── save_service.dart
│   ├── world_map_generator.dart
│   └── generation/
└── ui/
    ├── screens/
    └── widgets/
```

Key UI/game entry screens:
- `lib/ui/screens/game_wrapper.dart`
- `lib/ui/screens/game_screen.dart`
- `lib/ui/screens/world_map_screen.dart`

---

## Assets

Configured asset roots in `pubspec.yaml`:
- `assets/audio/`
- `assets/textures/`
- `assets/images/icons/`
- `assets/images/icons/effects/`
- `assets/images/icons/entities/`
- `assets/images/icons/items/`
- `assets/images/icons/monsters/`
- `assets/images/icons/tiles/`

---

## Notes on Non-Used Packages

The following are intentionally not part of the current dependency graph:
- `flame_bloc`
- `flame_rive`
- `flame_svg`
- `shared_preferences`
- `directed_graph`
- `responsive_builder`

Add them only when corresponding runtime features are actually implemented.

---

## Links

- [ARCHITECTURE.md](ARCHITECTURE.md) — system-level structure and data flow
- [ROADMAP.md](ROADMAP.md) — active priorities and unfinished phases