# ARCHITECTURE

> Current architecture for the running game, including world map flow, portal traversal, and generation systems.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
│   ├── core.d

*[truncated — see source for full prompt]*