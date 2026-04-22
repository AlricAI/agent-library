# Card Properties

> Card properties are values defined in the card's JSON data that are handled automatically by the game engine.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Card Properties

Card properties are values defined in the card's JSON data that are handled automatically by the game engine. **You do not need to implement these in card code.**

## Table of Contents

-   [Example JSON data](#example-json-data)
-   [House](#house)
-   [Power](#power)
-   [Armor](#armor)
-   [Aember Bonus](#aember-bonus)
-   [Enhancements](#enhancements)
-   [Accessing Properties in Code](#accessing-properties-in-code)
-   [Properties on Gigantics](#properties-on-gigantics)

## Example JSON data

```json
{
    "id": "example",
    "name": "Example",
    "house": "brobnar",
    "type": "creature",
    "power": 8,
    "armor": 2,
    "amber": 1,
    "enhancements": ["aember", "draw", "capture", "damage"]
}
```

## House

The house determines which house must be active to play or use the card.

-   Defined in JSON as `"house": "housename"` (lowercase)
-   Valid houses include: `brobnar`, `dis`, `logos`, `mars`, `sanctum`, `shadows`, `untamed`, `saurian`, `staralliance`, `unfathomable`, `ekwidon`, `geistoid`, `skyborn`
-   Accessed via `card.house` (current house, may be modified) or `card.printedHouse`
-   Cards with house enhancements can be played/used as if they belong to an additional house
-   Some effects can change a card's house temporarily

## Power

Power determines how much damage a creature deals when it fights. If a creature has equal or greater damage than its power then it is destroyed.

-   Defined in JSON as `"power": X`
-   Accessed via `card.power` (includes modifiers) or `card.printedPower`
-   Modified by effects like `ability.effects.modifyPower(amount)`

## Armor

Armor reduces damage dealt to a creature. Each point of armor prevents 1 damage per turn.

-   Defined in JSON as `"armor": X`
-   Armor "resets" at the start of each turn
-   Accessed via `card.armor` (includes modifiers) or `card.printedArmor`
-   Modified by effects like `ability.effects.modifyArmor(amount)`

## Aember Bonus

The aember bonus (Æ icons in the card'

*[truncated — see source for full prompt]*