# DIPLOMACY PHASE3

> This document describes the Phase 3 diplomacy improvements implemented in the game, building on Phase 1's Trust, Favors, and Promises systems and Phas

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Diplomacy Enhancement - Phase 3

This document describes the Phase 3 diplomacy improvements implemented in the game, building on Phase 1's Trust, Favors, and Promises systems and Phase 2's Grievances, Claims, and Specialized Alliances to add advanced diplomacy features.

## Overview

Phase 3 adds sophisticated diplomatic mechanics that enable complex international relations:

1. **Diplomatic Currency (DIP)** - Tradeable influence points earned through diplomatic actions
2. **International Council** - Global governance with voting and resolutions
3. **Dynamic Incidents** - Random diplomatic crises that can escalate to war
4. **Peace Conferences** - Multi-party negotiations for ending wars
5. **Advanced Espionage** - Covert operations affecting diplomacy

These systems work together with Phase 1 and Phase 2 features to create a comprehensive diplomatic simulation.

## Diplomatic Currency System

### What are Diplomatic Influence Points (DIP)?

DIP is a tradeable currency that represents a nation's diplomatic capital and influence on the world stage. Unlike favors (which are bilateral), DIP is a universal resource that can be spent on various diplomatic actions.

### DIP Scale

- **Capacity**: 200 points (default)
- **Starting DIP**: 50 points
- **Per-turn Income**: 5-30+ DIP based on various factors

### Earning DIP

**Base Income:**
- Base per turn: 5 DIP
- High-level alliances (Level 3+): +2 DIP per alliance
- Council membership (permanent/elected): +10 DIP
- Peace years (5+ consecutive peace turns): +1 DIP

**One-Time Rewards:**
- Successful mediation: +15 DIP
- Broker peace between nations: +20 DIP
- Resolve diplomatic incident: +10 DIP
- Host peace conference: +25 DIP
- Successful council resolution: +15 DIP

**DIP Income Example:**
```
Nation with:
- Base income: 5 DIP
- 2 high-level alliances: +4 DIP
- Council membership: +10 DIP
- Recent mediation: +15 DIP (one-time)
Total: 19 DIP per turn + bonuses
```

### Spending DIP

**Council Actions:**
- Call council 

*[truncated — see source for full prompt]*