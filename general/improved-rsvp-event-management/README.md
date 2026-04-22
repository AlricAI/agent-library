# Improved Rsvp Event Management

> ## Overview

This specification defines enhanced components for RSVP interactions and event management within YouAndINotAI, focusing on mobile-first d

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Improved RSVP and Event Management Component Specifications

## Overview

This specification defines enhanced components for RSVP interactions and event management within YouAndINotAI, focusing on mobile-first design, accessibility, and streamlined user experiences that encourage real-world community engagement.

## Design Goals

1. **Mobile-First Interactions**: Optimized touch targets and gesture-based controls
2. **Clear Status Communication**: Visual indicators for RSVP status and event details
3. **Accessibility Compliance**: WCAG 2.1 AA compliant components
4. **Performance Optimized**: Efficient rendering and minimal data usage
5. **Trust-Building**: Transparent controls with clear feedback

## RSVPButtonGroup Component

### Purpose

Provides standardized RSVP status selection with visual feedback and loading states.

### Component Structure

```jsx
<RSVPButtonGroup
  eventId={string}
  currentStatus={'going'|'maybe'|'not-going'|null}
  onStatusChange={(status) => void}
  size={'sm'|'md'|'lg'}
  variant={'segmented'|'individual'}
  loading={boolean}
  disabled={boolean}
  eventCapacity={{
    current: number,
    max: number | null
  }}
/>
```

### Props

| Prop             | Type   | Default     | Description                                         |
| ---------------- | ------ | ----------- | --------------------------------------------------- |
| `eventId`        | string | required    | Unique identifier for the event                     |
| `currentStatus`  | string | null        | Current RSVP status ('going', 'maybe', 'not-going') |
| `onStatusChange` | func   | required    | Callback when status changes                        |
| `size`           | string | 'md'        | Button size ('sm', 'md', 'lg')                      |
| `variant`        | string | 'segmented' | Display style ('segmented', 'individual')           |
| `loading`        | bool   | false       | Loading state indicator                             |
| `disabled`       | bool   | fal

*[truncated — see source for full prompt]*