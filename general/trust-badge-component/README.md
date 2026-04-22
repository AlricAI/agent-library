# Trust Badge Component

> ## Component Name

TrustBadge

## Overview

A visual indicator that communicates platform trust signals to users, showing the safety and verification 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TrustBadge Component Specification

## Component Name

TrustBadge

## Overview

A visual indicator that communicates platform trust signals to users, showing the safety and verification status of other users, events, and organizations. This component reinforces the platform's commitment to genuine community and responsible interaction.

## Props/State

### Props

| Prop        | Type                                            | Required | Description                                 |
| ----------- | ----------------------------------------------- | -------- | ------------------------------------------- |
| type        | 'user' \| 'event' \| 'organization'             | Yes      | Type of entity being verified               |
| status      | 'verified' \| 'reported' \| 'safe' \| 'pending' | Yes      | Current trust status                        |
| entityId    | string                                          | Yes      | Unique identifier for the entity            |
| onReport    | Function                                        | No       | Handler for reporting concerns              |
| size        | 'sm' \| 'md' \| 'lg'                            | No       | Visual size variant (default: 'md')         |
| showTooltip | boolean                                         | No       | Display explanatory tooltip (default: true) |

### State

| State          | Type    | Description               |
| -------------- | ------- | ------------------------- |
| tooltipVisible | boolean | Tooltip visibility state  |
| isReporting    | boolean | Report submission state   |
| reportSuccess  | boolean | Report submission success |

## Behavior Description

### Initial Load

1. Display appropriate icon and color based on status
2. Apply proper ARIA attributes for accessibility
3. Initialize event listeners for hover/focus interactions
4. Set up keyboard navigation support

### Interaction Patterns

1. **Hover/Focus**: Show tooltip with detailed status explanation
2. **Click**:

*[truncated — see source for full prompt]*