# Community Event Card Component

> ## Component Name

CommunityEventCard

## Overview

A card component displaying community event information with key details to help users quickly und

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CommunityEventCard Component Specification

## Component Name

CommunityEventCard

## Overview

A card component displaying community event information with key details to help users quickly understand what the event is about, when and where it's happening, and how to participate. Designed with mobile-first principles and accessibility in mind to facilitate real-world connections.

## Props/State

### Props

| Prop             | Type                                  | Required | Description                                    |
| ---------------- | ------------------------------------- | -------- | ---------------------------------------------- |
| event            | CommunityEvent                        | Yes      | Event data object containing all event details |
| variant          | 'standard' \| 'compact' \| 'featured' | No       | Visual variant (default: 'standard')           |
| onRSVP           | function                              | No       | Callback when user clicks RSVP button          |
| onDetail         | function                              | No       | Callback when user clicks for more details     |
| friendsAttending | Array<User>                           | No       | List of friends attending the event            |

### CommunityEvent Interface

```typescript
interface CommunityEvent {
  id: string;
  title: string;
  description: string;
  date: Date;
  startTime: string; // HH:mm format
  endTime: string; // HH:mm format
  location: {
    name: string;
    address?: string;
    latitude?: number;
    longitude?: number;
  };
  organizer: {
    name: string;
    avatarUrl: string;
  };
  category: 'meetup' | 'volunteer' | 'workshop' | 'social' | 'outdoor' | 'learning';
  maxAttendees: number;
  currentAttendees: number;
  isOnline: boolean;
  imageUrl?: string;
  tags: Array<string>;
  accessibilityFeatures: Array<'wheelchair' | 'asl' | 'captioning' | 'sensory' | 'service_animal'>;
  safetyGuidelines: Array<'mask_required' | 'vaccination_r

*[truncated — see source for full prompt]*