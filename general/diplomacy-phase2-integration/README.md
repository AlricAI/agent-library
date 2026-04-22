# DIPLOMACY PHASE2 INTEGRATION

> ## Overview

This document explains how to integrate Phase 2 diplomacy features (Grievances, Claims, and Specialized Alliances) into gameplay. The cod

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Diplomacy Phase 2 - Integration Guide

## Overview

This document explains how to integrate Phase 2 diplomacy features (Grievances, Claims, and Specialized Alliances) into gameplay. The code for these features exists but requires proper integration into game events.

## Current Status

✅ **Implemented:**
- Type definitions (grievancesAndClaims.ts, specializedAlliances.ts)
- Utility functions (grievancesAndClaimsUtils.ts, specializedAlliancesUtils.ts)
- UI components (GrievancesAndClaimsDisplay.tsx, SpecializedAllianceDisplay.tsx)
- Game state support (Nation interface updated)
- Integration module (diplomacyPhase2Integration.ts)
- AI actions updated (aiDiplomacyActions.ts)

⚠️ **Needs Integration:**
- Hook into attack/nuke handlers
- Call per-turn updates
- Display in UI

## Integration Points

### 1. Attack Events

When a nation attacks another, create appropriate grievances:

```typescript
import { onSurpriseAttack, onCivilianCasualties } from '@/lib/diplomacyPhase2Integration';

// After an attack is executed:
onSurpriseAttack(victim, attacker, currentTurn);

// After nuclear strike causing casualties:
const casualties = oldPopulation - newPopulation;
onCivilianCasualties(victim, attacker, casualties, currentTurn);
```

**Location:** `src/pages/Index.tsx` around lines 2948-2951 (nuclear detonation handler)

### 2. Diplomacy Actions

The AI diplomacy functions have been updated to support Phase 2. To enable:

```typescript
import { aiFormAlliance, aiBreakTreaties, aiImposeSanctions } from '@/lib/aiDiplomacyActions';

// When calling these functions, pass currentTurn:
aiFormAlliance(actor, target, logFn, currentTurn, 'military');
aiBreakTreaties(actor, target, logFn, reason, currentTurn);
aiImposeSanctions(actor, target, logFn, currentTurn);
```

**Location:** `src/pages/Index.tsx` around line 3346-3367 (AI decision tree)

### 3. Per-Turn Updates

Each turn, update grievances, claims, and alliances:

```typescript
import { updateGrievancesAndClaimsPerTurn } from 

*[truncated — see source for full prompt]*