# DIPLOMACY PHASE1

> This document describes the Phase 1 diplomacy improvements implemented in the game, including Trust, Favors, and Diplomatic Promises systems.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Diplomacy Enhancement - Phase 1

This document describes the Phase 1 diplomacy improvements implemented in the game, including Trust, Favors, and Diplomatic Promises systems.

## Overview

Phase 1 adds three interconnected diplomatic systems that create deeper, more meaningful relationships between nations:

1. **Trust System** - Long-term relationship reliability (0-100)
2. **Favors System** - Short-term diplomatic obligations
3. **Diplomatic Promises** - Binding commitments that build or destroy trust

## Trust System

### What is Trust?

Trust represents the long-term reliability and trustworthiness between two nations. Unlike the relationship score (which represents current sentiment), trust measures whether a nation keeps its word and honors commitments.

### Trust Scale
- **0-100 scale** (starts at 50 - neutral)
- **80+**: Trusted Partner (won't be rivaled, best trade deals)
- **60-79**: Reliable (good diplomatic terms)
- **40-59**: Neutral (standard diplomacy)
- **20-39**: Untrustworthy (expensive proposals, alliance unlikely)
- **0-19**: Treacherous (won't ally, poor terms)

### How Trust Changes

**Trust Increases:**
- Honoring treaties (+5)
- Keeping promises (+10)
- Defending allies (+8)
- Long alliances (+0.5 per turn)
- Rejecting enemy offers (+3)

**Trust Decreases:**
- Breaking treaties (-25)
- Breaking promises (-20)
- Surprise attacks (-40)
- Betraying allies (-35)
- Refusing to help when called (-15)

**Natural Decay:**
- Trust slowly drifts toward neutral (50) over time
- Above 50: -0.5 per turn
- Below 50: +0.5 per turn

### Trust Effects

**High Trust (80+)**
- Nations won't rival you
- Better trade deals
- Cheaper diplomatic proposals
- AI more likely to accept your proposals
- +25 bonus to proposal acceptance scores

**Low Trust (30-)**
- Nations won't form alliances
- Expensive diplomatic actions
- AI unlikely to accept proposals
- -25 penalty to proposal acceptance scores

## Favors System

### What are Favors?

Favors represent short-term

*[truncated — see source for full prompt]*