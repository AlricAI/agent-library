# Spy System Leader Integration

> This document describes how leader abilities can interact with the spy system to provide unique strategic advantages.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Spy System - Leader Ability Integration

This document describes how leader abilities can interact with the spy system to provide unique strategic advantages.

## Leader Ability Categories for Espionage

### 1. Spy Enhancement Abilities
These abilities directly improve spy performance:

- **Spymaster's Network** - All spies gain +20 skill and +15% success chance for 5 turns
- **Perfect Cover** - Next recruited spy starts at Elite level with perfect cover identity
- **Ghost Protocol** - All active spies become undetectable for 3 turns
- **Master Recruiter** - Recruit 3 spies instantly with no cooldown or cost

### 2. Counter-Intelligence Abilities
These abilities protect against enemy spies:

- **Paranoid Security** - Automatic detection of all enemy spies for 4 turns
- **Counter-Espionage Sweep** - Instantly capture all enemy spies in your territory
- **Diplomatic Immunity** - Your spies cannot be caught for 3 turns
- **Deep Cover** - One spy becomes permanent double agent in enemy nation

### 3. Intelligence Manipulation
These abilities affect intelligence and information:

- **Disinformation Campaign** - Feed false intel to all enemy spies (causes their missions to fail)
- **Signal Intelligence** - Reveal all active enemy spy missions and their targets
- **Cryptographic Breakthrough** - Read all diplomatic communications for 5 turns
- **Intelligence Sharing** - Gain copies of all intelligence gathered by allied nations

### 4. Sabotage & Assassination
Enhanced versions of spy missions:

- **Coordinated Strike** - Launch 3 sabotage missions simultaneously with guaranteed success
- **Wetwork Authorization** - Next assassination mission has 100% success, 0% detection
- **Industrial Espionage** - Steal all completed research from target nation at once
- **Regime Change** - Rig election and assassinate leader in single mission

## Implementation Examples

### Example 1: Existing Leader with Spy Enhancement

```typescript
// Nyarlathotep already has 'Master Deceiver' 

*[truncated — see source for full prompt]*