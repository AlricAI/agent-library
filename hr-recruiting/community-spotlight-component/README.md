# Community Spotlight Component

> ## Component Name

CommunitySpotlight

## Overview

A carousel component showcasing real users and their meaningful connections formed through YouAndI

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CommunitySpotlight Component Specification

## Component Name

CommunitySpotlight

## Overview

A carousel component showcasing real users and their meaningful connections formed through YouAndINotAI, emphasizing the platform's impact on building genuine community relationships.

## Props/State

### Props

| Prop       | Type                                     | Required | Description                             |
| ---------- | ---------------------------------------- | -------- | --------------------------------------- |
| stories    | Array<CommunityStory>                    | Yes      | Collection of community stories         |
| autoplay   | boolean                                  | No       | Enable/disable autoplay (default: true) |
| interval   | number                                   | No       | Autoplay interval in ms (default: 5000) |
| showDots   | boolean                                  | No       | Show navigation dots (default: true)    |
| showArrows | boolean                                  | No       | Show navigation arrows (default: true)  |
| variant    | 'standard' \| 'compact' \| 'testimonial' | No       | Visual variant                          |

### CommunityStory Interface

```typescript
interface CommunityStory {
  id: string;
  user: {
    name: string;
    avatarUrl: string;
    location: string;
  };
  connection: {
    name: string;
    avatarUrl: string;
  };
  story: string;
  impact: {
    hoursSpentTogether: number;
    activitiesDone: number;
    friendshipDuration: string; // e.g., "8 months"
  };
  media?: {
    type: 'image' | 'video';
    url: string;
    caption?: string;
  };
  tags: Array<'meetup' | 'volunteer' | 'friends' | 'mentor' | 'neighborhood'>;
}
```

### State

| State        | Type    | Description                   |
| ------------ | ------- | ----------------------------- |
| currentIndex | number  | Currently visible story index |
| isPlaying    | boolean | Autoplay status               |
| isHovered 

*[truncated — see source for full prompt]*