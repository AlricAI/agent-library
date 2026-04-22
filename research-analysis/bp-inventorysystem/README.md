# BP InventorySystem

> A data-driven, expandable inventory system with item definitions, slots, stacking, and equipment.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Inventory System Blueprint

A data-driven, expandable inventory system with item definitions, slots, stacking, and equipment.

## Overview

Uses Data Tables for item definitions, structures for runtime instances, and components for inventory management. Supports stacking, weight limits, equipment slots, and action usage.

## Files

- `S_ItemData` (Structure) - Static item definition
- `S_InventoryItem` (Structure) - Runtime instance
- `E_ItemCategory` (Enum) - Weapon, Consumable, Material, Quest, etc.
- `E_ItemRarity` (Enum) - Common, Uncommon, Rare, Epic, Legendary
- `DT_Items` (Data Table) - All item definitions
- `BP_InventoryComponent` (Actor Component)
- `BP_EquipmentComponent` (Actor Component)
- `WBP_InventoryGrid` (User Widget)
- `WBP_InventorySlot` (User Widget)

---

## Data Structures

### S_ItemData (Structure)

| Variable | Type | Description |
|----------|------|-------------|
| ItemID | Name | Unique identifier |
| DisplayName | String | UI name |
| Description | String | Lore text |
| Icon | Texture2D | UI image |
| Category | E_ItemCategory | Type classification |
| Rarity | E_ItemRarity | Quality tier |
| MaxStackSize | Integer | 1 for equipment, 99 for consumables |
| BaseValue | Integer | Sell price |
| Weight | Float | Inventory load |
| bCanBeUsed | Boolean | Has use action |
| bCanBeEquipped | Boolean | Has equipment slot |
| EquipSlot | E_EquipSlot | Where it goes |
| UseEffect | TSoftClass | Blueprint to spawn on use |
| Stats | S_ItemStats | Bonus stats if equipped |

### S_ItemStats (Structure)

| Variable | Type |
|----------|------|
| HealthBonus | Float |
| DamageBonus | Float |
| DefenseBonus | Float |
| SpeedBonus | Float |
| MagicBonus | Float |

### S_InventoryItem (Structure)

| Variable | Type | Description |
|----------|------|-------------|
| ItemID | Name | Reference to S_ItemData |
| Quantity | Integer | Current stack amount |
| InstanceData | Map(String, String) | Per-item variables |

---

## E_ItemCategory (Enum)

```
Non

*[truncated — see source for full prompt]*