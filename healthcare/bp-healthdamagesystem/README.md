# BP HealthDamageSystem

> A comprehensive, component-based health and damage system with events, modifiers, and team support.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Health and Damage System Blueprint

A comprehensive, component-based health and damage system with events, modifiers, and team support.

## Overview

This pattern uses an Actor Component for health management, allowing any actor to have health without complex inheritance hierarchies. Implements damage types, events, and team-based damage filtering.

## Files

- `BP_HealthComponent` (Actor Component)
- `BP_DamageTypeBase` (Blueprint)
- `BP_HealthInterface` (Blueprint Interface, optional)
- `BP_HealthBarWidget` (User Widget)
- `BP_ExampleCharacter` (Implementation)

---

## BP_HealthComponent

**Type:** Actor Component  
**Replication:** Replicated (Multiplayer support)

### Variables

#### Core Health

| Name | Type | Default | Flags |
|------|------|---------|-------|
| MaxHealth | Float | 100.0 | Replicated, EditAnywhere |
| CurrentHealth | Float | 100.0 | Replicated, EditAnywhere |
| bIsDead | Boolean | False | Replicated |
| bInvulnerable | Boolean | False | EditAnywhere |
| bCanRegenerate | Boolean | False | EditAnywhere |
| RegenRate | Float | 5.0 | EditAnywhere (HP/sec) |
| RegenDelay | Float | 3.0 | EditAnywhere (after damage) |
| RegenTimer | Timer Handle | - | Private |

#### Team System

| Name | Type | Default | Description |
|------|------|---------|-------------|
| TeamId | Integer | 0 | 0 = neutral, 1 = player, 2 = enemy, etc. |
| bIgnoreFriendlyFire | Boolean | False | Block same-team damage |

#### Events (Event Dispatchers)

| Name | Inputs | Description |
|------|--------|-------------|
| OnHealthChanged | CurrentHealth, MaxHealth, Delta | Fires on any health change |
| OnDamaged | DamageAmount, DamageType, Instigator, Causer | Fires when taking damage |
| OnHealed | HealAmount, Source | Fires when healing applied |
| OnDeath | DamageType, Instigator | Fires when health reaches 0 |
| OnRevive | - | Fires when revived |

---

## Event Graph

### Begin Play

```
[Event BeginPlay]
    │
    ├──► [IsServer]
    │       │
    │       └──► [True] ──► [

*[truncated — see source for full prompt]*