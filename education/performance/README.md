# PERFORMANCE

> > Lessons learned from [Pump.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Performance Strategy Guide

> Lessons learned from [Pump.fun's 10x React Native startup improvement](https://medium.com/@pumpfun) and how they apply to crypto-vision.

## Table of Contents

1. [The Problem](#the-problem)
2. [Server-Side: WebSocket Broadcast Throttling](#server-side-websocket-broadcast-throttling)
3. [Mobile: Replace Polling with WebSocket + Client-Side Throttling](#mobile-replace-polling-with-websocket--client-side-throttling)
4. [Mobile: Memoize StyleSheet Creation](#mobile-memoize-stylesheet-creation)
5. [Mobile: Performance Telemetry](#mobile-performance-telemetry)
6. [Dashboard: Tailwind Class Validation](#dashboard-tailwind-class-validation)
7. [Architecture Principles](#architecture-principles)
8. [Checklist for New Features](#checklist-for-new-features)

---

## The Problem

Real-time crypto apps face a specific performance challenge: **high-frequency data meets expensive rendering**. Pump.fun documented receiving ~1,000 trades/second per coin, with screens showing 10+ coins simultaneously — potentially 10,000 events/second.

Our crypto-vision platform faces the same class of problem:
- CoinCap WebSocket emits continuous price ticks for 10+ coins
- The mobile app shows 50 coins on the Markets screen
- The dashboard shows real-time prices, charts, and sentiment

### What Pump.fun Found

| Metric | Before | After |
|--------|--------|-------|
| CSS interop CPU usage | 3.5% | 0.01% |
| App startup (iOS) | 1.5s | 110ms |
| Route change speed | baseline | ~10% faster |

Their key insight: **runtime style computation was the dominant cost**, and moving it to build-time eliminated it entirely.

---

## Server-Side: WebSocket Broadcast Throttling

**File:** `src/lib/ws.ts`

### What We Changed

CoinCap sends price ticks as fast as they arrive. Previously, every tick was immediately broadcast to all connected clients. Now, price updates are **buffered and flushed at 5 Hz** (200ms intervals):

```
CoinCap tick (100+/sec) → pendingPrices buffer → flus

*[truncated — see source for full prompt]*