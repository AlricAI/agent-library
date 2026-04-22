# Real World Meetups Enhancement

> ## Overview

Enhance the real-world meetup discovery and creation experience to make it more engaging, accessible, and effective for connecting users 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Design Specification: Enhanced Real-World Meetup Features

## Overview

Enhance the real-world meetup discovery and creation experience to make it more engaging, accessible, and effective for connecting users offline.

## Current State Analysis

The current Events page provides basic functionality for creating and discovering meetups but lacks:

- Visual appeal and engagement
- Geographic filtering capabilities
- Social proof elements
- Mobile-optimized discovery flows
- Integration with user profiles/preferences

## Design Goals

1. **Mobile-First Discovery** - Optimize for touch interactions and small screens
2. **Geo-Aware Filtering** - Enable location-based discovery with visual maps
3. **Social Engagement** - Show social proof through participant counts and friend connections
4. **Rich Media** - Support images and detailed descriptions for events
5. **Seamless Creation** - Simplify the event creation process with smart defaults

## Proposed Enhancements

### 1. Enhanced Discovery Interface

```
┌─────────────────────────────────────┐
│  Nearby Meetups            [Filter] │
├─────────────────────────────────────┤
│                                     │
│  [MAP VIEW]                         │
│  ┌─────────────────────────────┐   │
│  │ ○ Coffee & Conversations    │   │
│  │   Central Park • 2.3mi      │   │
│  │   8 attending               │   │
│  └─────────────────────────────┘   │
│                                     │
│  ┌─────────────────────────────┐   │
│  │ ○ Tech Volunteer Day        │   │
│  │   Library • 0.8mi           │   │
│  │   12/20 attending           │   │
│  └─────────────────────────────┘   │
│                                     │
└─────────────────────────────────────┘
```

### 2. Event Card Enhancement

- Add event imagery support
- Include weather considerations
- Show friend attendance indicators
- Add accessibility information
- Include estimated cost/category tags

### 3. Improved Creation Flow

```
Step 1: What                    S

*[truncated — see source for full prompt]*