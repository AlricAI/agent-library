---
name: ARCHITECTURE
description: Current architecture for the running game, including world map flow, portal traversal, and generation systems.
model: claude-sonnet-4-5
---
# Nyxis — Architecture Overview

Current architecture for the running game, including world map flow, portal traversal, and generation systems.

---

## System Diagram

```mermaid
graph TB
    subgraph presentation [PresentationLayer]
        gameWrapper[GameWrapper]
        flutterUi[FlutterUI]
        flameComponents[FlameComponents]
        worldMapUi[WorldMapUI]
    end

    subgraph gameLayer [GameLayer]
        nyxisGame[NyxisGame]
        floorManager[FloorManager]
        turnSystem[TurnSystem]
        combatSystem[CombatSystem]
        monsterBehaviorSystem[MonsterBehaviorSystem]
    end

    subgraph dataLayer [DataAndCore]
        gameState[GameState]
        worldMap[WorldMap]
        models[EntityAndWorldModels]
        eventBus[EventBus]
    end

    subgraph servicesLayer [Services]
        pathfinding[PathfindingService]
        generation[GenerationPipeline]
        saveService[SaveService]
        worldMapGenerator[WorldMapGenerator]
        audioService[AudioService]
    end

    subgraph configLayer [RegistriesAndConfig]
        monsterRegistry[MonsterRegistry]
        itemRegistry[ItemRegistry]
        locationRegistry[LocationRegistry]
        portalRegistry[PortalRegistry]
    end

    gameWrapper --> flutterUi
    gameWrapper --> worldMapUi
    flutterUi --> nyxisGame
    flameComponents --> nyxisGame
    worldMapUi --> gameWrapper
    gameWrapper --> floorManager
    floorManager --> worldMap
    floorManager --> nyxisGame
    nyxisGame --> turnSystem
    turnSystem --> combatSystem
    turnSystem --> monsterBehaviorSystem
    monsterBehaviorSystem --> pathfinding
    turnSystem --> eventBus
    nyxisGame --> gameState
    gameState --> worldMap
    gameState --> models
    saveService --> gameState
    generation --> locationRegistry
    generation --> portalRegistry
    worldMapGenerator --> gameState
    models --> monsterRegistry
    models --> itemRegistry
```

---

## Directory Structure

```
lib/
├── main.dart
├── core/
│   ├── core.dart
│   ├── event_bus.dart
│   └── events.dart
├── config/
│   ├── constants.dart
│   ├── monster_config.dart
│   ├── item_config.dart
│   ├── location_config.dart
│   ├── portal_definition.dart
│   └── portal_registry.dart
├── models/
│   ├── game_state.dart
│   ├── entities/
│   │   ├── entity.dart
│   │   ├── player.dart
│   │   ├── monster.dart
│   │   ├── item.dart
│   │   ├── world_object.dart
│   │   └── portal.dart
│   └── world/
│       ├── map.dart
│       ├── tile.dart
│       ├── location.dart
│       └── world_map.dart
├── game/
│   ├── nyxis_game.dart
│   ├── components/
│   │   ├── player_component.dart
│   │   ├── monster_component.dart
│   │   ├── item_component.dart
│   │   └── tile_component.dart
│   ├── services/
│   │   ├── component_manager.dart
│   │   ├── floor_manager.dart
│   │   └── ...
│   └── systems/
│       ├── turn_system.dart
│       ├── combat_system.dart
│       └── monster_behavior_system.dart
├── services/
│   ├── audio_service.dart
│   ├── pathfinding_service.dart
│   ├── save_service.dart
│   ├── world_map_generator.dart
│   └── generation/
│       ├── generation.dart
│       ├── generator_registry.dart
│       ├── location_generator.dart
│       ├── surface_generator.dart
│       ├── dungeon_generator.dart
│       ├── portal_placement.dart
│       └── steps/
├── ui/
│   ├── screens/
│   │   ├── game_wrapper.dart
│   │   ├── main_menu_screen.dart
│   │   ├── game_screen.dart
│   │   ├── inventory_screen.dart
│   │   └── world_map_screen.dart
│   └── widgets/
│       ├── hud_widget.dart
│       ├── action_toolbar.dart
│       ├── health_bar.dart
│       └── minimap_widget.dart
```

---

## Key Architectural Patterns

### 1. Registry-Driven Content

Entity definitions and world routing are data-driven (`MonsterRegistry`, `ItemRegistry`, `LocationRegistry`, `PortalRegistry`), keeping balance and content changes outside core game loop logic.

### 2. Event-Driven Systems

Gameplay systems publish and consume events through `EventBus` (`lib/core/event_bus.dart`), reducing direct coupling between systems, rendering components, and UI reactions.

### 3. Turn-Based Orchestration

`TurnSystem` coordinates player actions, combat resolution, and monster turns, while visual interpolation is handled by Flame components.

### 4. Location-Oriented World Flow

`GameWrapper` owns the canonical `GameState`, switches between `WorldMapScreen` and `GameScreen`, and routes transitions through `FloorManager`. Location gameplay, surface exits, and overworld travel all operate on that single shared state.

### 5. Composable Generation Pipeline

Location generation uses structured generation context + steps + registries so dungeon and surface generation can share orchestration while varying behavior.

### 6. Overworld-Driven Surface Visuals

Surface locations inherit their base ground tile type from the owning overworld `MapTile` terrain. The flow is `WorldMap.findLocationTile()` -> `FloorManager` terrain resolution -> `SurfaceGenerator` -> `Tile.surface(...)`, which keeps surface visuals aligned with the top-level map without changing encounter or spawn logic.

### 7. Layered Navigation Model

Navigation is organized as separate conceptual layers rather than one flat graph:

- `WorldMap` is the high-level routing layer.
- `Surface locations` are enterable local exploration spaces attached to world map nodes.
- `Underground locations` are separate interior spaces connected to surfaces by portals.
- `Dungeon floors` are vertical slices inside one underground location and are connected only by stairs.

```mermaid
flowchart TB
    subgraph worldMapLayer [WorldMapLayer]
        worldHub["WorldMapRegion"]
        worldNodeA["EnterableWorldNode"]
        worldNodeB["EnterableWorldNode"]
    end

    subgraph surfaceLayer [SurfaceLocationLayer]
        surfaceA["SurfaceLocation"]
        surfaceB["SurfaceLocation"]
    end

    subgraph undergroundLayer [UndergroundLocationLayer]
        subgraph undergroundA [UndergroundLocation]
            undergroundA0["Floor0_EntranceLayer"]
            undergroundA1["LowerFloor"]
            undergroundA2["DeeperFloor"]
        end

        subgraph undergroundB [UndergroundLocation]
            undergroundB0["Floor0_EntranceLayer"]
            undergroundB1["LowerFloor"]
        end
    end

    worldHub --- worldNodeA
    worldHub --- worldNodeB

    worldNodeA -->|"enter location"| surfaceA
    worldNodeB -->|"enter location"| surfaceB

    surfaceA <-->|"portal"| undergroundA0
    surfaceB <-->|"portal"| undergroundB0

    undergroundA0 <-->|"stairs"| undergroundA1
    undergroundA1 <-->|"stairs"| undergroundA2

    undergroundB0 <-->|"stairs"| undergroundB1
```

This model keeps three transition types distinct:

- `world map travel` moves between world nodes
- `portal travel` moves between sibling locations on different layers
- `stairs travel` moves within a single underground location across floors

---

## Core Runtime Flow

```mermaid
sequenceDiagram
    participant input as PlayerInput
    participant wrapper as GameWrapper
    participant game as NyxisGame
    participant turn as TurnSystem
    participant combat as CombatSystem
    participant ai as MonsterBehaviorSystem
    participant bus as EventBus
    participant render as ComponentsAndUI

    input->>wrapper: worldMap enter or resume
    input->>game: action request
    game->>turn: submit player action
    turn->>combat: resolve attack when needed
    turn->>ai: process monster turns
    turn->>bus: publish gameplay events
    bus->>render: movement, damage, death, state updates
    render->>input: await next player action
```

## Surface Visual Flow

```mermaid
graph LR
    worldMapTile[WorldMapTileTerrain] --> floorManager[FloorManager]
    floorManager --> surfaceGenerator[SurfaceGenerator]
    surfaceGenerator --> tileFactory[Tile.surface]
    tileFactory --> tileComponent[TileComponent]
```

---

## Links

- [TECH_STACK.md](TECH_STACK.md) — active dependencies and stack guidance
- [ROADMAP.md](ROADMAP.md) — active priorities and unfinished phases