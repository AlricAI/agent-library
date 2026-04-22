# Spy System Implementation Guide

> This guide explains how to integrate the spy system into the Vector War Games application.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Spy System - Implementation Guide

This guide explains how to integrate the spy system into the Vector War Games application.

## Table of Contents
1. [Quick Start](#quick-start)
2. [Hook Integration](#hook-integration)
3. [UI Integration](#ui-integration)
4. [Turn Processing](#turn-processing)
5. [Notification System](#notification-system)
6. [Testing](#testing)
7. [Balancing](#balancing)

---

## Quick Start

### 1. Install Dependencies
The spy system uses existing dependencies. No new packages required.

### 2. Import Required Modules

```typescript
// In your main game component (e.g., Index.tsx)
import { useSpyNetwork } from '@/hooks/useSpyNetwork';
import { SpyNetworkPanel } from '@/components/SpyNetworkPanel';
import { initializeSpyNetwork } from '@/lib/spyNetworkUtils';
```

### 3. Initialize Spy Network for New Games

```typescript
// When creating a new nation or starting a game
const initializeNation = (nation: Nation): Nation => {
  return {
    ...nation,
    spyNetwork: initializeSpyNetwork(),
  };
};
```

---

## Hook Integration

### Basic Setup

```typescript
// In your main game component
const spyNetwork = useSpyNetwork({
  currentTurn: gameState.turn,
  getNation: (id: string) => nations.find(n => n.id === id),
  getNations: () => nations,
  updateNation: (id: string, updates: Partial<Nation>) => {
    setNations(prev => prev.map(n =>
      n.id === id ? { ...n, ...updates } : n
    ));
  },
  updateNations: (updates: Map<string, Partial<Nation>>) => {
    setNations(prev => prev.map(nation => {
      const update = updates.get(nation.id);
      return update ? { ...nation, ...update } : nation;
    }));
  },
  getGameState: () => gameState,
  onLog: (message, tone) => {
    // Log to game log
    addGameLog(message, tone);
  },
  onToast: (payload) => {
    // Show toast notification
    toast(payload);
  },
});
```

### Available Methods

```typescript
// Recruitment
spyNetwork.recruitSpy(playerNationId, {
  cover: 'diplomat',
  targetNation:

*[truncated — see source for full prompt]*