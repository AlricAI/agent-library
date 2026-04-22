# DOCTRINE SYSTEM

> ## Overview

The Doctrine System enhances the base Cold War game by making military doctrines dynamic and impactful throughout gameplay. Instead of be

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Doctrine System Documentation

## Overview

The Doctrine System enhances the base Cold War game by making military doctrines dynamic and impactful throughout gameplay. Instead of being a one-time choice at game start, doctrines now:

1. **Affect diplomatic relationships** - Compatible doctrines improve relations, incompatible ones hinder them
2. **Generate incidents** - Random events challenge your doctrine commitment and force meaningful choices
3. **Track doctrine drift** - Your actions can shift you toward different doctrines over time

---

## System Components

### 1. Doctrine Incidents & Crises

**What are they?**
Random events that occur during gameplay, challenging your doctrine commitment and forcing you to make difficult choices.

**How they work:**
- Each doctrine (MAD, Defense, First Strike, Détente) has 3-4 unique incidents
- Incidents have probability checks each turn based on game state
- When triggered, player must choose from 2-3 options
- Each choice has consequences (resources, relationships, doctrine shift, etc.)
- Minimum 3 turns between incidents to avoid overwhelming player

**Example Incidents:**

**MAD:**
- False Alarm at Early Warning Station (critical)
- Ally Requests Nuclear Umbrella (major)
- Aging Arsenal Reliability Concerns (major)

**Defense:**
- ABM Test Fails Publicly (major)
- Budget Crisis: Defense vs Offense (major)
- ABM Technology Breakthrough (opportunity)

**First Strike:**
- Intelligence: Enemy Preparing Strike (critical)
- General Advocates Immediate Attack (major)
- Public Ethics Debate on First Strike (major)

**Détente:**
- Hardliners Demand Tougher Stance (critical)
- Enemy Caught Cheating on Treaty (critical)
- Peace Dividend Opportunity (opportunity)

**Code Locations:**
- Types: `src/types/doctrineIncidents.ts`
- Incident Data: `src/lib/doctrineIncidentData.ts`
- System Logic: `src/lib/doctrineIncidentSystem.ts`
- UI Component: `src/components/DoctrineIncidentModal.tsx`

---

### 2. Doctrine Diplomacy Integration


*[truncated — see source for full prompt]*