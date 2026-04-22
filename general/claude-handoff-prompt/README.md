# CLAUDE HANDOFF PROMPT

> ## Project Context

You are working on a complex Cold War grand strategy game built with React, TypeScript, Vite, and Tailwind CSS. The game features 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Cold War Strategy Game - Morale & Political System Implementation Handoff

## Project Context

You are working on a complex Cold War grand strategy game built with React, TypeScript, Vite, and Tailwind CSS. The game features nuclear strategy, diplomacy, espionage, and now a comprehensive political simulation system.

## What Has Been Completed (Just Now)

### Phase 3 Implementation: Morale & Political Events System

I have just implemented **Priority 1 (Visual Feedback)** and **Priority 2 (Policy System)** of the comprehensive political system. Here's what exists:

#### ✅ Already Existing Core Systems (Before This Session)

1. **Governance Metrics Hook** (`src/hooks/useGovernance.ts`)
   - Tracks morale, public opinion, cabinet approval, election timer
   - Automatic metric decay and drift simulation
   - Political event triggering system
   - 6 major political events with branching outcomes
   - AI auto-resolution for non-player nations

2. **Political Events** (`src/lib/events/politicalEvents.ts`)
   - Election Year Showdown
   - Nationwide Morale Crisis
   - Cabinet Scandal
   - Mass Uprising
   - Government Legitimacy Crisis
   - Military Loyalty Questioned
   - Each with multiple player choices and probabilistic outcomes

3. **Political News System** (`src/lib/politicalNews.ts`)
   - Dynamic news generation based on stability
   - AI personality-driven international commentary
   - Election news coverage
   - Tension-building atmosphere news

4. **Regime Change System** (`src/lib/regimeChange.ts`)
   - AI nations can experience regime changes
   - Based on instability, morale, and approval ratings
   - New leaders/personalities assigned after change

5. **Production/Military Effects**
   - `calculateMoraleProductionMultiplier()`: 0.7x to 1.25x based on morale
   - `calculateMoraleRecruitmentModifier()`: 0.75x to 1.2x based on morale
   - Already integrated into `src/lib/gamePhaseHandlers.ts`

6. **Basic UI** (`src/components/governance/GovernanceEventDialog.t

*[truncated — see source for full prompt]*