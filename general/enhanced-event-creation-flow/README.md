# Enhanced Event Creation Flow

> ## Overview

This specification outlines an improved event creation experience for YouAndINotAI that emphasizes mobile-first design, location awarenes

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Enhanced Event Creation Flow Specification

## Overview

This specification outlines an improved event creation experience for YouAndINotAI that emphasizes mobile-first design, location awareness, and streamlined form completion. The goal is to reduce friction while maintaining security and trust.

## Design Goals

1. **Mobile-First**: Optimized touch interactions and minimal form fields
2. **Location-Aware**: Smart defaults with explicit user consent
3. **Streamlined**: Reduce steps from idea to published event
4. **Inclusive**: Accessible to all users regardless of ability
5. **Trust-Building**: Clear privacy controls and consent mechanisms

## User Journey

### Current State Analysis

From reviewing `Events.tsx` and `MeetupsDiscovery.tsx`, the current flow requires:

- Title input
- Description text area
- Location field
- Date/time picker
- Max attendees (optional)
- Separate create button

### Proposed Enhanced Flow

#### Step 1: Event Intent

```
┌─────────────────────────────────────────────────┐
│  ← Create Event                                ≡│
├─────────────────────────────────────────────────┤
│                                                 │
│  What kind of gathering are you planning?       │
│                                                 │
│  [_community cleanup_] [book club_] [potluck_]  │
│  [volunteer drive_] [game night_] [other_]      │
│                                                 │
│  ┌─────────────────────────────────────────────┐ │
│  │ Describe your event (required)              │ │
│  │ We're organizing a neighborhood cleanup...  │ │
│  └─────────────────────────────────────────────┘ │
│                                                 │
│  [ Continue ]                                   │
│                                                 │
└─────────────────────────────────────────────────┘
```

#### Step 2: Location & Timing

```
┌─────────────────────────────────────────────────┐
│  ← Back            Create Event               ≡ 

*[truncated — see source for full prompt]*