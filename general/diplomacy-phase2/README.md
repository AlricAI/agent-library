# DIPLOMACY PHASE2

> This document describes the Phase 2 diplomacy improvements implemented in the game, building on Phase 1's Trust, Favors, and Promises systems to add Grievances & Claims and Specialized Alliances.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Diplomacy Enhancement - Phase 2

This document describes the Phase 2 diplomacy improvements implemented in the game, building on Phase 1's Trust, Favors, and Promises systems to add Grievances & Claims and Specialized Alliances.

> **⚠️ INTEGRATION REQUIRED:** The code for Phase 2 features is fully implemented, but requires integration into game events. See **[DIPLOMACY_PHASE2_INTEGRATION.md](./DIPLOMACY_PHASE2_INTEGRATION.md)** for a complete integration guide.

## Overview

Phase 2 adds depth to diplomatic relationships through:

1. **Grievances System** - Historical wrongs that complicate diplomacy
2. **Claims System** - Territorial and resource claims that justify conflicts
3. **Specialized Alliance Types** - Four distinct alliance types with unique benefits

These systems work together with Phase 1 features to create a rich, multi-layered diplomatic experience.

## Grievances System

### What are Grievances?

Grievances are historical wrongs or complaints that one nation holds against another. They represent lasting diplomatic damage from past actions and make cooperation more difficult.

### Grievance Types

**Severe Grievances:**
- **Betrayed Ally** (-45 relationship, -50 trust, 60 turns)
- **War Crimes** (-50 relationship, -45 trust, 80 turns)
- **Surprise Attack** (-35 relationship, -40 trust, 40 turns)
- **Civilian Casualties** (-40 relationship, -30 trust, 60 turns)
- **Broken Treaty** (-30 relationship, -35 trust, 50 turns)

**Major Grievances:**
- **Broken Promise** (-15 relationship, -20 trust, 30 turns)
- **Territorial Seizure** (-25 relationship, -15 trust, 50 turns)

**Moderate Grievances:**
- **Sanction Harm** (-10 relationship, -5 trust, 25 turns)
- **Espionage Caught** (-12 relationship, -10 trust, 20 turns)

**Minor Grievances:**
- **Refused Aid** (-5 relationship, -8 trust, 15 turns)

### How Grievances Work

**Creation:**
- Grievances are automatically created when certain actions occur
- Each grievance applies immediate trust and relationsh

*[truncated — see source for full prompt]*