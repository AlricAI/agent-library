# Activity Feed Components

> ## Overview

A comprehensive activity feed system for YouAndINotAI that displays community activities, updates, and social interactions in a chronolog

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Activity Feed Components Specification

## Overview

A comprehensive activity feed system for YouAndINotAI that displays community activities, updates, and social interactions in a chronological, engaging, and privacy-respecting manner.

## Component Structure

### ActivityFeed

Primary container for displaying chronological activities

### ActivityItem

Individual activity display with context and actions

### ActivityComposer

Interface for creating new activities/posts

### ActivityFilters

Controls for filtering activity feed content

### ActivityEngagement

Engagement metrics and actions for activities

## Component Specifications

### ActivityFeed

#### Props

| Prop        | Type            | Required | Description                       |
| ----------- | --------------- | -------- | --------------------------------- |
| activities  | Array<Activity> | Yes      | Array of activity objects         |
| currentUser | User            | Yes      | Currently logged in user          |
| onLoadMore  | Function        | No       | Callback to load more activities  |
| onRefresh   | Function        | No       | Callback to refresh feed          |
| isLoading   | Boolean         | No       | Whether loading activities        |
| hasMore     | Boolean         | No       | Whether more activities available |
| filters     | ActivityFilters | No       | Current filter settings           |

#### Activity Interface

```typescript
interface Activity {
  id: string;
  type:
    | 'event_created'
    | 'event_attended'
    | 'new_connection'
    | 'volunteer_completed'
    | 'post_created'
    | 'achievement_unlocked';
  actor: User;
  target?: User | Event | Group;
  content?: string;
  media?: Array<MediaItem>;
  timestamp: Date;
  privacy: 'public' | 'connections' | 'private';
  engagement: {
    likes: number;
    comments: number;
    shares: number;
    likedByCurrentUser: boolean;
  };
  context?: {
    location?: string;
    group?: string;
    event?: string;
  };
}
`

*[truncated — see source for full prompt]*