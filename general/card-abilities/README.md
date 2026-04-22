# Card Abilities

> This document describes how card abilities are defined in Keyteki.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Card Abilities

This document describes how card abilities are defined in Keyteki. All card abilities are defined in the `setupCardAbilities(ability)` method of a card class.

## Table of Contents

-   [Basic Structure](#basic-structure)
-   [Ability Types](#ability-types)
    -   [play()](#play)
    -   [reap()](#reap)
    -   [fight()](#fight)
    -   [beforeFight()](#beforefight)
    -   [destroyed()](#destroyed)
    -   [action()](#action)
    -   [omni()](#omni)
    -   [persistentEffect()](#persistenteffect)
    -   [whileAttached()](#whileattached)
    -   [reaction()](#reaction)
    -   [interrupt()](#interrupt)
    -   [scrap()](#scrap)
    -   [fate()](#fate)
    -   [prophecyInterrupt()](#prophecyinterrupt)
    -   [prophecyReaction()](#prophecyreaction)
-   [Ability Properties](#ability-properties)
    -   [Conditions](#conditions)
    -   [Optional](#optional)
    -   [Targeting](#targeting)
    -   [Chaining Effects with "then"](#chaining-effects-with-then)

## Basic Structure

Every card follows this general pattern to set up its abilities:

```javascript
const Card = require('../../Card.js');

class CardName extends Card {
    // Card text goes here as a comment
    setupCardAbilities(ability) {
        this.abilityType({
            // ability properties
        });
    }
}

CardName.id = 'card-id';

module.exports = CardName;
```

## Ability Types

### play()

Triggered abilities that activate after the card is played. Bonus icons are resolved before play abilities.

```javascript
// Play: Gain 2A.
this.play({
    gameAction: ability.actions.gainAmber({ amount: 2 })
});
```

```javascript
// Play: Capture 3A.
this.play({
    gameAction: ability.actions.capture({ amount: 3 })
});
```

```javascript
// Play: Ready and fight with a friendly creature.
this.play({
    target: {
        cardType: 'creature',
        controller: 'self',
        gameAction: ability.actions.sequential([ability.actions.ready(), ability.actions.fight()])
    },
    effect: 

*[truncated — see source for full prompt]*