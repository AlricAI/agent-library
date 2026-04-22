# BP InteractionSystem

> A modular, raycast-based interaction system for player-to-world interactions.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Interaction System Blueprint

A modular, raycast-based interaction system for player-to-world interactions.

## Overview

This pattern creates a reusable interaction system where the player can look at and interact with objects in the world. Uses interfaces for maximum flexibility.

## Files

- `BP_InteractionInterface` (Blueprint Interface)
- `BP_InteractionComponent` (Actor Component)
- `BP_InteractableBase` (Parent Actor)
- `BP_PlayerCharacter` (Implementation)

---

## BP_InteractionInterface

**Type:** Blueprint Interface

### Functions

#### Interact
- **Inputs:** InteractingActor (Actor)
- **Outputs:** None
- **Description:** Called when player activates interaction

#### CanInteract
- **Inputs:** InteractingActor (Actor)
- **Outputs:** Boolean
- **Description:** Check if interaction is currently possible

#### GetInteractionPrompt
- **Inputs:** None
- **Outputs:** String
- **Description:** Returns UI text for interaction hint

#### OnBeginFocus
- **Inputs:** None
- **Outputs:** None
- **Description:** Called when player looks at interactable

#### OnEndFocus
- **Inputs:** None
- **Outputs:** None
- **Description:** Called when player looks away

---

## BP_InteractionComponent

**Type:** Actor Component  
**Attaches to:** Player Character

### Variables

| Name | Type | Default | Description |
|------|------|---------|-------------|
| InteractionDistance | Float | 300.0 | Max interaction range |
| InteractionCheckRate | Float | 0.1 | Seconds between checks |
| InteractionChannel | ECollisionChannel | Visibility | Trace channel |
| CurrentInteractable | Interface | None | Currently focused object |

### Event Graph

#### Event BeginPlay
```
[Event BeginPlay]
    │
    └──► [Set Timer by Function Name]
         ├── Function Name: "CheckForInteraction"
         ├── Time: InteractionCheckRate
         ├── Looping: True
         └── Initial Start Delay: 0.0
```

#### CheckForInteraction (Custom Event)
```
[Line Trace by Channel]
    ├── Start: [Get World Locati

*[truncated — see source for full prompt]*