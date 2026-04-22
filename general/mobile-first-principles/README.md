# Mobile First Principles

> ## Overview

This document establishes the foundational principles for designing mobile-first experiences at YouAndINotAI. Our platform is used primar

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# YouAndINotAI Mobile-First Design Principles

## Overview

This document establishes the foundational principles for designing mobile-first experiences at YouAndINotAI. Our platform is used primarily on mobile devices, and all design decisions must prioritize the mobile experience while ensuring graceful adaptation to larger screens.

## Core Principles

### 1. Mobile-First Mindset

#### Start with Constraints

- Begin design process with smallest screen size (320px width)
- Consider limited bandwidth and processing power
- Account for touch-based interactions vs. mouse/keyboard
- Design for portrait orientation as default
- Prioritize essential functionality

#### Progressive Enhancement

- Add features and complexity for larger screens
- Never remove core functionality on smaller screens
- Enhance visual treatments on larger screens
- Utilize additional screen real estate meaningfully
- Maintain consistent interaction patterns

### 2. Touch-First Interaction Design

#### Touch Target Optimization

- All interactive elements minimum 48px in smallest dimension
- Touch targets spaced minimum 8px apart
- Primary actions placed within thumb-friendly zones
- Secondary actions positioned appropriately for reach
- Gestural interactions designed for discoverability

#### Thumb-Friendly Interfaces

- Primary actions in bottom third of screen
- Navigation elements sized for easy tapping
- Close/reverse actions placed near their triggers
- Scrolling preferred over pagination where possible
- Modal dialogs with clear exit paths

#### Gesture Integration

- Swipe gestures for common actions (delete, archive, etc.)
- Long press for secondary actions
- Pull-to-refresh for content updates
- Pinch zoom for image/content viewing
- Shake gestures used sparingly and with clear purpose

### 3. Performance-Conscious Design

#### Speed Perception

- Instant visual feedback for all user actions
- Skeleton screens for loading content
- Progressive disclosure of complex information
- Minim

*[truncated — see source for full prompt]*