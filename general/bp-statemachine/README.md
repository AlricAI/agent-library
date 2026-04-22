# BP StateMachine

> A robust, enum-based finite state machine (FSM) for character AI, player states, game flow, and any sequential logic.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# State Machine Blueprint

A robust, enum-based finite state machine (FSM) for character AI, player states, game flow, and any sequential logic.

## Overview

Uses Enums to define states, with enter/exit/update hooks for each state. Supports transitions, state history, and event handling. Can be extended for AI behaviors, player movement modes, UI flows, or game state management.

## Files

- `E_ExampleState` (Enum) - Define your states
- `BP_StateMachineComponent` (Actor Component) - Reusable FSM engine
- `BP_StateMachineInterface` (Blueprint Interface) - Optional callbacks
- `BP_ExampleAIController` (Implementation)

---

## E_ExampleState (Enum)

**Use Case: AI Enemy States**

```
Idle            // Waiting for player
Patrol          // Following waypoint path
Alert           // Heard something, investigating
Chase           // Spotted player, pursuing
Attack          // In range, attacking
Stunned         // Hit by player, temporarily disabled
Dead            // Defeated
```

**Use Case: Player Movement States**

```
Idle
Walking
Sprinting
Crouching
Jumping
Falling
Landed
Swimming
Flying
Dead
```

---

## BP_StateMachineComponent

**Type:** Actor Component  
**Replication:** Replicated

### Variables

| Name | Type | Default | Description |
|------|------|---------|-------------|
| CurrentState | Enum | First value | Active state |
| PreviousState | Enum | None | For state revert |
| bCanChangeState | Boolean | true | Lock during transitions |
| bLogStateChanges | Boolean | false | Debug logging |
| StateData | Map(Enum, Struct) | Empty | Per-state config |

### Event Dispatchers

| Name | Inputs | Description |
|------|--------|-------------|
| OnStateEntered | NewState, OldState | Fires after entering state |
| OnStateExited | OldState, NewState | Fires before leaving state |
| OnStateUpdate | CurrentState, DeltaTime | Fires every tick |
| OnStateChanged | NewState, OldState | Wrapper for enter/exit |

### Core Functions

#### Initialize State Machine

```
[Ev

*[truncated — see source for full prompt]*