# MORALE POLITICAL SYSTEM IMPLEMENTATION

> ## Executive Summary

This document outlines the implementation plan for the comprehensive Morale & Political Events System. This system adds critical

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Morale & Political Events System - Implementation Plan (Phase 3)

## Executive Summary

This document outlines the implementation plan for the comprehensive Morale & Political Events System. This system adds critical realism and strategic depth by simulating domestic politics, public opinion, and their effects on national capabilities.

## Current State Analysis

### ✅ Already Implemented

1. **Core Governance Metrics System** (`useGovernance` hook)
   - Morale (0-100): National morale affecting production and military recruitment
   - Public Opinion (0-100): Population's view of government
   - Cabinet Approval (0-100): Leadership support from political elite
   - Election Timer: Countdown to next election cycle
   - Instability: Measure of political chaos

2. **Production & Military Effects**
   - `calculateMoraleProductionMultiplier()`: Morale affects production (0.7x to 1.25x)
   - `calculateMoraleRecruitmentModifier()`: Morale affects unit recruitment (0.75x to 1.2x)
   - Already integrated into game phase handlers

3. **Political Events System**
   - 6 major event types with branching outcomes
   - Events: Election Cycle, Morale Crisis, Cabinet Scandal, Mass Uprising, Government Crisis, Military Unrest
   - Each event has multiple player choices with probabilistic outcomes
   - Events affect governance metrics and can trigger cascading consequences

4. **UI Components**
   - `GovernanceEventDialog`: Modal for presenting political events and choices
   - Event cards showing current metrics and outcome probabilities
   - News ticker integration

5. **Political News & Media**
   - Dynamic news generation based on nation stability
   - AI personality-driven international commentary
   - Tension-building news for atmosphere
   - Flashpoint aftermath coverage

6. **Regime Change System**
   - AI nations can experience regime changes based on instability
   - New leaders and personalities assigned
   - Military losses during transitions
   - News coverage of regime

*[truncated — see source for full prompt]*