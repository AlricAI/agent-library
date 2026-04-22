# Great Old Ones Week 3 Summary

> ## Overview

Phase 1, Week 3 of the Great Old Ones campaign focuses on **Ritual Site Operations**, implementing the tactical and strategic layer that 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Great Old Ones - Week 3 Implementation Summary

## Overview

Phase 1, Week 3 of the Great Old Ones campaign focuses on **Ritual Site Operations**, implementing the tactical and strategic layer that allows players to manage ritual sites, deploy hybrid unit rosters, and engage with procedurally generated missions.

## Implemented Features

### 1. Ritual Site Mechanics (`src/lib/ritualSiteMechanics.ts`)

#### Site Upgrade System
- **Four Tier Progression**: Shrine → Temple → Nexus → Gateway
- Each tier provides:
  - Increased power storage and generation
  - Higher-tier entity summoning capabilities
  - Enhanced defense bonuses
  - Unlocked special abilities

#### Biome-Based Bonuses
Six distinct biomes, each with unique strategic advantages:
- **Ocean**: Deep One summoning, excellent concealment (+50%), lower sanity harvesting
- **Mountain**: Maximum ritual power (+50%), stellar channeling, sky signs
- **Urban**: Maximum sanity harvesting (+80%), lower concealment
- **Ruins**: Ancient power resonance (+40%), artifact discovery, primordial connections
- **Desert**: Isolation for dangerous rituals (+60% concealment), buried temples
- **Forest**: Natural cover (+40%), druidic rituals, Shub-Niggurath affinity

#### Defensive Mechanics
- **Glamour Veil**: Reduces detection by up to 40% (requires Temple tier+)
- **Defensive Wards**: Reduces raid damage by up to 50% and ritual disruption by 60% (requires Nexus tier+)
- Biome concealment bonuses stack with defensive measures

#### Geostrategic Site Placement
Intelligent site placement system evaluating:
- Regional corruption levels
- Existing cultist presence
- Investigation heat risk
- Cultural compatibility with doctrine
- Biome availability

### 2. Hybrid Unit Roster (`src/lib/unitRoster.ts`)

#### Cultist Types
Three-tier progression system:

**Street-Level Initiates**
- Basic recruitment and reconnaissance
- Low ritual skill (1), moderate infiltration (2)
- 5 sanity fragments/turn harvesting
- Available for: recruiting

*[truncated — see source for full prompt]*