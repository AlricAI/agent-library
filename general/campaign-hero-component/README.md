# Campaign Hero Component

> ## Component Name

CampaignHero

## Overview

Primary hero component for the Q3 "Connection with Purpose" campaign landing page.

## Props/State

### 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CampaignHero Component Specification

## Component Name

CampaignHero

## Overview

Primary hero component for the Q3 "Connection with Purpose" campaign landing page.

## Props/State

### Props

| Prop        | Type                                  | Required | Description                |
| ----------- | ------------------------------------- | -------- | -------------------------- |
| variant     | 'volunteer' \| 'community' \| 'story' | Yes      | Visual theme variant       |
| headline    | string                                | Yes      | Main campaign headline     |
| subheadline | string                                | Yes      | Supporting text            |
| ctaText     | string                                | Yes      | Call-to-action button text |
| imageUrl    | string                                | Yes      | Background/image URL       |
| impactStat  | object                                | No       | Statistical impact data    |

### State

| State     | Type    | Description                 |
| --------- | ------- | --------------------------- |
| isVisible | boolean | Controls entrance animation |
| isLoaded  | boolean | Image loading state         |
| isHovered | boolean | Mouse hover state           |

## Behavior Description

### Initial Load

1. Component renders with skeleton loader
2. Background image loads with progressive enhancement
3. Content fades in with staggered animation
4. CTA button becomes focusable after load

### User Interactions

1. **CTA Button Click**: Navigate to sign-up flow
2. **Background Click**: Navigate to event browsing
3. **Impact Stat Click**: Navigate to impact page
4. **Hover States**: Subtle elevation effect on interactive elements

### Responsive Behavior

1. **Mobile (<768px)**: Single column layout, full-width button
2. **Tablet (768px-1024px)**: Split layout with adjusted proportions
3. **Desktop (>1024px)**: Maximum container width with side padding

### Performance Considerations

1. Lazy load backgr

*[truncated — see source for full prompt]*