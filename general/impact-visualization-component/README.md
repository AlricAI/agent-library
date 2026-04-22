# Impact Visualization Component

> ## Component Name

ImpactVisualization

## Overview

Dynamic visualization component displaying real-time community impact metrics for the Q3 campaign

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ImpactVisualization Component Specification

## Component Name

ImpactVisualization

## Overview

Dynamic visualization component displaying real-time community impact metrics for the Q3 campaign.

## Props/State

### Props

| Prop            | Type              | Required | Description                                  |
| --------------- | ----------------- | -------- | -------------------------------------------- |
| stats           | Array<ImpactStat> | Yes      | Collection of impact statistics              |
| title           | string            | No       | Section heading                              |
| description     | string            | No       | Supporting text                              |
| isLoading       | boolean           | No       | Loading state indicator                      |
| refreshInterval | number            | No       | Auto-refresh interval in ms (default: 30000) |

### ImpactStat Interface

```typescript
interface ImpactStat {
  id: string;
  value: number | string;
  label: string;
  icon: string; // Icon identifier
  trend?: 'up' | 'down' | 'neutral'; // Optional trend indicator
  change?: number; // Percentage change
}
```

### State

| State          | Type          | Description                  |
| -------------- | ------------- | ---------------------------- |
| currentIndex   | number        | Current carousel slide index |
| isAutoPlaying  | boolean       | Auto-rotation enabled state  |
| formattedStats | Array<Object> | Stats formatted for display  |

## Behavior Description

### Initial Load

1. Display skeleton loaders while fetching data
2. Animate counter values from 0 to actual amounts
3. Show introductory tooltip for first-time users
4. Start auto-rotation timer if applicable

### Data Refresh

1. Poll API at specified interval for updated stats
2. Smooth transition between old and new values
3. Visual indicator when data updates occur
4. Error handling for failed API requests

### User Controls

1. **Carousel Nav

*[truncated — see source for full prompt]*