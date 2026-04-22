# Game Actions

> Game actions are the atomic operations that modify game state.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Game Actions Reference

Game actions are the atomic operations that modify game state. They are accessed through `ability.actions.*` in card ability definitions.

## Table of Contents

-   [Basic Usage](#basic-usage)
-   [Card Actions](#card-actions)
    -   [archive({ target })](#archive-target-)
    -   [capture({ amount })](#capture-amount-)
    -   [dealDamage({ amount, target })](#dealdamage-amount-target-)
    -   [destroy({ target })](#destroy-target-)
    -   [discard({ target })](#discard-target-)
    -   [enrage({ target })](#enrage-target-)
    -   [exalt({ amount })](#exalt-amount-)
    -   [exhaust({ target })](#exhaust-target-)
    -   [fight({ target })](#fight-target-)
    -   [heal({ amount, target })](#heal-amount-target-)
    -   [moveToFlank({ target, left })](#movetoflank-target-left-)
    -   [placeAmber({ amount })](#placeamber-amount-)
    -   [placeUnder({ parent })](#placeunder-parent-)
    -   [purge({ target })](#purge-target-)
    -   [putIntoPlay({ target })](#putintoplay-target-)
    -   [ready({ target })](#ready-target-)
    -   [reap({ target })](#reap-target-)
    -   [removeStun({ target })](#removestun-target-)
    -   [removeWard({ target })](#removeward-target-)
    -   [returnToDeck({ bottom, shuffle })](#returntodeck-bottom-shuffle-)
    -   [returnToHand({ target })](#returntohand-target-)
    -   [sacrifice({ target })](#sacrifice-target-)
    -   [stun({ target })](#stun-target-)
    -   [swap({ origin })](#swap-origin-)
    -   [use({ target })](#use-target-)
    -   [ward({ target })](#ward-target-)
-   [Player Actions](#player-actions)
    -   [chosenDiscard({ amount })](#chosendiscard-amount-)
    -   [discardAtRandom({ amount })](#discardatrandom-amount-)
    -   [discardTopOfDeck({ amount })](#discardtopofdeck-amount-)
    -   [draw({ amount })](#draw-amount-)
    -   [forgeKey({ modifier })](#forgekey-modifier-)
    -   [gainAmber({ amount })](#gainamber-amount-)
    -   [gainChains({ amount })](#gainchains-amount

*[truncated — see source for full prompt]*