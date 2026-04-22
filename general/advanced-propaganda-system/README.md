# ADVANCED PROPAGANDA SYSTEM

> A comprehensive propaganda warfare system for Vector War Games featuring psychological operations, infiltration networks, and ideological weaponization.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Advanced Propaganda System

A comprehensive propaganda warfare system for Vector War Games featuring psychological operations, infiltration networks, and ideological weaponization.

## Overview

The Advanced Propaganda System extends the existing cultural warfare mechanics with three sophisticated subsystems:

1. **Useful Idiots** - Recruit influential individuals to unwittingly spread your propaganda
2. **Phobia Campaigns** - Weaponize fear to destabilize enemy populations
3. **Religious Weapons** - Deploy ideological narratives to unite your people and divide theirs

## System Components

### 1. Useful Idiots System

Recruit influential individuals from target nations who unwittingly become propaganda assets.

#### Idiot Types

| Type | Credibility | Influence | Cost | Description |
|------|------------|-----------|------|-------------|
| **Academic** | 85 | 60 | 70 | University professors, intellectuals |
| **Journalist** | 70 | 80 | 60 | Media personalities, reporters |
| **Politician** | 50 | 90 | 80 | Local politicians, activists |
| **Celebrity** | 40 | 95 | 75 | Entertainers, influencers |
| **Business Leader** | 75 | 70 | 85 | CEOs, industry leaders |
| **Religious Leader** | 80 | 85 | 90 | Clergy, spiritual guides |
| **Influencer** | 35 | 85 | 50 | Social media personalities |

#### Mechanics

**Recruitment Process:**
- Base cost: 50 intel (modified by type)
- Takes 2-4 turns to complete
- Success chance: 20-90% (based on relationships, cultural influence, intel strength)
- Discovery risk: 10% per turn during recruitment

**Active Operations:**
- Generate propaganda value each turn based on: `(influence × credibility × alignment) / 10000`
- Maintenance cost: `influence × 0.1` intel per turn
- Effects on target nation:
  - Increases instability by propaganda value × 0.1
  - Reduces morale by propaganda value × 0.05
  - Increases cultural influence by propaganda value × 0.2
  - Reduces pop loyalty by 1 per turn (random pops)

**Exposure Risk:**
- Base ris

*[truncated — see source for full prompt]*