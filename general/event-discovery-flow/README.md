# Event Discovery Flow

> ## Overview

A comprehensive design specification for the event discovery experience within YouAndINotAI, connecting users with meaningful community e

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Event Discovery Flow Specification

## Overview

A comprehensive design specification for the event discovery experience within YouAndINotAI, connecting users with meaningful community events through an intuitive, accessible, and mobile-first interface. This specification integrates the CommunityEventCard, RSVPButtonGroup, and other supporting components into a cohesive flow.

## User Journey Map

### Phase 1: Discovery

1. User browses event feed or uses search/filter
2. Events presented as CommunityEventCards
3. Key information visible at a glance
4. Quick actions available (RSVP, Details)

### Phase 2: Evaluation

1. User taps for more information
2. Card expands to show full event details
3. Accessibility and safety features highlighted
4. Friend connections shown

### Phase 3: Decision

1. User selects RSVP status using RSVPButtonGroup
2. Immediate visual confirmation of selection
3. Optional addition to personal calendar
4. Sharing options for inviting friends

### Phase 4: Follow-up

1. Calendar reminders sent before event
2. Pre-event preparation information
3. Post-event reflection prompts
4. Connection suggestions based on shared events

## Screen Flows

### Home Feed with Events Section

```
┌─────────────────────────────────────────────────────────┐
│  YouAndINotAI                                          ≡ │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  Upcoming Events Near You                               │
│                                                         │
│  [CommunityEventCard]                                   │
│  [CommunityEventCard]                                   │
│  [CommunityEventCard]                                   │
│                                                         │
│  [View All Events]                                      │
│                                                         │
└──────────────────────────────────────────────────────

*[truncated — see source for full prompt]*