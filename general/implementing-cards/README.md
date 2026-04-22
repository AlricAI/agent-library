# Implementing Cards

> This guide covers the basics of implementing KeyForge cards in Keyteki.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Implementing Cards

This guide covers the basics of implementing KeyForge cards in Keyteki. For detailed ability documentation, see:

-   [Card Abilities](card-abilities.md) - Ability types and their properties
-   [Game Actions](game-actions.md) - All available `ability.actions.*` methods
-   [Keywords](keywords.md) - Keywords handled automatically by the engine
-   [Testing Cards](testing-cards.md) - How to write tests

## Table of Contents

-   [Getting Started](#getting-started)
    -   [Testing in the UI](#testing-in-the-ui)
-   [File Structure](#file-structure)
-   [Basic Card Template](#basic-card-template)
-   [Keywords](#keywords)
-   [Persistent Effects](#persistent-effects)
    -   [Basic Persistent Effect](#basic-persistent-effect)
    -   [Conditional Effects](#conditional-effects)
    -   [Target Controllers](#target-controllers)
    -   [Upgrade Effects](#upgrade-effects)
    -   [Player Effects](#player-effects)
-   [Actions](#actions)
    -   [Basic Action](#basic-action)
    -   [Action with Target](#action-with-target)
    -   [Omni Actions](#omni-actions)
-   [Triggered Abilities](#triggered-abilities)
    -   [Reactions](#reactions)
    -   [Interrupts](#interrupts)
    -   [Trigger Events](#trigger-events)
-   [Targeting](#targeting)
    -   [Single Target](#single-target)
    -   [Multiple Targets](#multiple-targets)
    -   [Target Properties](#target-properties)
    -   [Card Conditions](#card-conditions)
-   [Costs](#costs)
-   [Lasting Effects](#lasting-effects)
    -   [Durations](#durations)
-   [Ability Limits](#ability-limits)

## Getting Started

To implement a card:

-   Find the card's data in `keyteki-json-data/packs/<Set>.json`
-   Create a file in `server/game/cards/<Set>/<CardName>.js`
-   Implement the card's abilities
-   Write tests in `test/server/cards/<Set>/<CardName>.spec.js`
-   Run and verify tests pass: `DEBUG_TEST=1 npm test -- test/server/cards/<Set>/<CardName>.spec.js`

### Testing in the UI

-   Start the server:

*[truncated — see source for full prompt]*