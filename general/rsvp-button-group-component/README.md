# Rsvp Button Group Component

> ## Component Name

RSVPButtonGroup

## Overview

A component providing intuitive RSVP (Yes, Maybe, No) controls for community events. Designed with cl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# RSVPButtonGroup Component Specification

## Component Name

RSVPButtonGroup

## Overview

A component providing intuitive RSVP (Yes, Maybe, No) controls for community events. Designed with clear visual feedback, accessibility compliance, and mobile-first interaction patterns to facilitate quick decision-making for event participation.

## Props/State

### Props

| Prop           | Type                                      | Required | Description                                 |
| -------------- | ----------------------------------------- | -------- | ------------------------------------------- |
| eventId        | string                                    | Yes      | Unique identifier for the event             |
| status         | 'going' \| 'maybe' \| 'not_going' \| null | No       | Current user RSVP status                    |
| onStatusChange | function                                  | No       | Callback when user changes RSVP status      |
| size           | 'sm' \| 'md' \| 'lg'                      | No       | Button size variation (default: 'md')       |
| disabled       | boolean                                   | No       | Disable all buttons (default: false)        |
| showLabels     | boolean                                   | No       | Show text labels on buttons (default: true) |
| variant        | 'segmented' \| 'individual'               | No       | Layout variant (default: 'segmented')       |

### State

| State        | Type                                      | Description                            |
| ------------ | ----------------------------------------- | -------------------------------------- |
| localStatus  | 'going' \| 'maybe' \| 'not_going' \| null | Local state mirroring props.status     |
| isLoading    | boolean                                   | Whether an RSVP action is in progress  |
| isSuccess    | boolean                                   | Whether the last action was successful |
| errorMessage | string        

*[truncated — see source for full prompt]*