# Keywords

> Keywords in KeyForge are special abilities that appear on cards.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Keywords

Keywords in KeyForge are special abilities that appear on cards. In Keyteki, most keywords are handled automatically by the game engine based on the card's JSON data - **you do not need to implement them in card code**.

## Table of Contents

-   [List of Keywords](#list-of-keywords)
    -   [Alpha](#alpha)
    -   [Assault X](#assault-x)
    -   [Deploy](#deploy)
    -   [Elusive](#elusive)
    -   [Entrenched](#entrenched)
    -   [Exalt](#exalt)
    -   [Graft](#graft)
    -   [Haunted](#haunted)
    -   [Hazardous X](#hazardous-x)
    -   [Invulnerable](#invulnerable)
    -   [Omega](#omega)
    -   [Overwhelmed](#overwhelmed)
    -   [Poison](#poison)
    -   [Skirmish](#skirmish)
    -   [Splash-Attack X](#splash-attack-x)
    -   [Taunt](#taunt)
    -   [Treachery](#treachery)
    -   [Versatile](#versatile)
-   [How Keywords Work](#how-keywords-work)
-   [Cards That Grant Keywords](#cards-that-grant-keywords)
-   [Cards That Reference Keywords](#cards-that-reference-keywords)

## List of Keywords

These keywords are parsed from the card's JSON data and implemented automatically. **Do not reimplement them in card JavaScript files.**

### Alpha

> **Alpha** - You can only play this card before doing anything else this step.

The card can only be played as the first card of your turn. Handled automatically by play restrictions.

### Assault X

> **Assault X** - Before this creature attacks, deal X damage to the attacked creature.

When this creature initiates a fight, it deals X damage to the defender before the fight damage is exchanged. Handled in the fight resolution logic. If the creature is destroyed by the assault damage, the fight does not proceed, after fight abilities do not trigger, but the creature is still considered to have been in a fight for the purposes of other effects.

### Deploy

> **Deploy** - This creature can be played to any position in your battleline (not just the flanks).

Normally creatures must be played to a flank. Depl

*[truncated — see source for full prompt]*