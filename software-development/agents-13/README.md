# AGENTS

> This guide covers implementing cards and game mechanics in the server codebase.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Server Implementation Guide

This guide covers implementing cards and game mechanics in the server codebase.

## Architecture Overview

### Core Classes

-   **Game** (`server/game/game.js`) - Main game controller; manages phases, players, and game state
-   **Card** (`server/game/Card.js`) - Base class for all cards; provides ability definition methods
-   **Player** (`server/game/player.js`) - Player state, hand, deck, discard, archives, creatures, artifacts
-   **EffectEngine** (`server/game/effectengine.js`) - Manages persistent effects and their application
-   **GameActions** (`server/game/GameActions/`) - Atomic game actions (deal damage, draw cards, etc.)

When making changes outside of the `cards/` dirs for implementing new game mechanics or adding new functionality to the core game engine, always update the relevant documentation in the `docs/` folder. If you notice gaps, mistakes, or outdated information in the documentation, take the time to update it accordingly.

When adding a new game action or mechanic, add tests to the core test files in `test/server/` (outside of `test/server/cards/`). This includes adding message tests to verify the correct game messages are produced.

### Card Implementation Reference

For detailed documentation with examples, see the `docs/` folder, which includes guides for card abilities, game actions, keywords, testing, and more.

## Code Style Conventions

-   Card classes extend `Card` and implement `setupCardAbilities(ability)`
-   Card ID is set as static property: `CardName.id = 'card-id';`
-   Export with `module.exports = CardName;`
-   Use arrow functions for conditions and callbacks
-   Comment the card text above `setupCardAbilities`
-   Always end files with a newline
-   When writing a templated effect or message, use placeholders like `{0}`, `{1}`, etc., and provide corresponding values to ensure proper formatting. Do not concatenate strings or use template literals for game messages.
-   Order object propertie

*[truncated — see source for full prompt]*