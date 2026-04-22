# Card Messages

> This document describes how to add descriptive log messages to card abilities.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Card Messages

This document describes how to add descriptive log messages to card abilities. Good messages help players understand what happened during a game.

## Table of Contents

-   [Basic Usage](#basic-usage)
-   [Properties](#properties)
    -   [effect / effectArgs](#effect--effectargs)
    -   [message / messageArgs](#message--messageargs)
-   [Default Messages](#default-messages)
    -   [When to Override Default Messages](#when-to-override-default-messages)
-   [Common Patterns](#common-patterns)
    -   [Adding Dynamic Values](#adding-dynamic-values)
    -   [Conditional Messages](#conditional-messages)
    -   [Then Effect Messages](#then-effect-messages)
    -   [Messages for Optional Actions](#messages-for-optional-actions)
    -   [Using preThenContext](#using-prethencontext)
    -   [preThenEvents for Multiple Targets](#prethenevents-for-multiple-targets)
    -   [Referencing `this` in effectArgs](#referencing-this-in-effectargs)
    -   [Appending Text Conditionally](#appending-text-conditionally)
    -   [Context Event Data](#context-event-data)
    -   [Revealing Cards with Conditional Text](#revealing-cards-with-conditional-text)
    -   [promptForSelect with messageArgs](#promptforselect-with-messageargs)
    -   [Pluralization in Messages](#pluralization-in-messages)
    -   [Raw String Values in effectArgs](#raw-string-values-in-effectargs)
    -   [Named Card References](#named-card-references)
    -   [Static messageArgs Values](#static-messageargs-values)
    -   [Computed Effects with Multiple Branches](#computed-effects-with-multiple-branches)
    -   [Multi-part Message Building](#multi-part-message-building)
-   [Best Practices](#best-practices)
-   [Quick Reference](#quick-reference)
-   [Using `target`](#using-target)
-   [Locales](#locales)

## Basic Usage

Card abilities support two messaging approaches:

-   **`effect` / `effectArgs`** - For primary abilities. Automatically prefixed with "{player} uses {card} to..."
-   **`mess

*[truncated — see source for full prompt]*