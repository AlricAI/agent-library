# Testing Cards

> This document explains how to write tests for cards.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Testing Cards

This document explains how to write tests for cards.

## Table of Contents

-   [Overview](#overview)
-   [Test File Structure](#test-file-structure)
-   [Setting Up Tests](#setting-up-tests)
    -   [setupTest Options](#setuptest-options)
    -   [Card State Setup](#card-state-setup)
    -   [Recommended Test Creatures](#recommended-test-creatures)
    -   [Moving Cards Between Zones](#moving-cards-between-zones)
    -   [Changing a Card's House](#changing-a-cards-house)
-   [Player Actions](#player-actions)
    -   [Playing Cards](#playing-cards)
    -   [Using Cards](#using-cards)
    -   [Responding to Prompts](#responding-to-prompts)
    -   [Prophecy Cards](#prophecy-cards)
    -   [Tide Manipulation](#tide-manipulation)
-   [Assertions](#assertions)
    -   [Prompt Assertions](#prompt-assertions)
    -   [Card Selection Assertions](#card-selection-assertions)
    -   [Card State Assertions](#card-state-assertions)
    -   [Player State Assertions](#player-state-assertions)
    -   [Chat Log Assertions](#chat-log-assertions)
-   [Card References](#card-references)
    -   [Basic Examples](#basic-examples)
    -   [Numbers in Card IDs](#numbers-in-card-ids)
    -   [Cards Starting with Numbers](#cards-starting-with-numbers)
    -   [Apostrophes in Card Names](#apostrophes-in-card-names)
    -   [Multiple Copies of the Same Card](#multiple-copies-of-the-same-card)
    -   [Gigantic Cards (Two-Part Cards)](#gigantic-cards-two-part-cards)
    -   [Finding Cards Explicitly](#finding-cards-explicitly)
-   [Common Patterns](#common-patterns)
    -   [Testing Play Abilities](#testing-play-abilities)
    -   [Testing Reap Abilities](#testing-reap-abilities)
    -   [Testing Fight Abilities](#testing-fight-abilities)
    -   [Testing Destroyed Abilities](#testing-destroyed-abilities)
    -   [Testing Action Abilities](#testing-action-abilities)
    -   [Testing Persistent Effects](#testing-persistent-effects)
    -   [Testing "Cannot" Restrictions](#tes

*[truncated — see source for full prompt]*