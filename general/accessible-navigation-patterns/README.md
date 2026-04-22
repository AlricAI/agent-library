# Accessible Navigation Patterns

> ## Overview

This specification defines accessible navigation patterns for switching between discovery (dating/feed) and events contexts within YouAnd

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Accessible Navigation Patterns for Discovery and Events Contexts

## Overview

This specification defines accessible navigation patterns for switching between discovery (dating/feed) and events contexts within YouAndINotAI, ensuring seamless transitions while maintaining platform accessibility standards and mobile-first design principles.

## Design Goals

1. **Seamless Context Switching**: Effortless movement between discovery and events
2. **Accessibility Compliance**: WCAG 2.1 AA compliance with keyboard/screen reader support
3. **Mobile-First Navigation**: Optimized for touch interfaces and small screens
4. **Consistent Mental Model**: Clear information architecture mapping
5. **Performance Optimized**: Fast navigation without page reloads

## Current Navigation Analysis

### Desktop Navigation (Sidebar)

- Permanent sidebar navigation with clear sections
- Icons with text labels for each major context
- Active state indication with color and styling
- Scrollable navigation for extensive item lists

### Mobile Navigation (Bottom Bar)

- Fixed position bottom navigation bar
- Icon-only or icon + text presentation
- Horizontal scrolling for overflow items
- Active state highlighting

### Contexts Identified

1. Discover (Swipe/Feed)
2. Concierge (AI Assistant)
3. Matches
4. Messages
5. Boards (Social Groups)
6. Events (Meetups)
7. Volunteer (Community Service)
8. Support
9. Impact (Metrics/Stats)

## Proposed Enhanced Navigation Patterns

### 1. Context Switcher Component

#### Purpose

Primary navigation control for switching between major platform contexts.

#### Component Structure

```jsx
<ContextSwitcher
  currentContext={'discover'|'events'|'matches'|'messages'|'boards'|'volunteer'|'support'|'impact'}
  onContextChange={(context) => void}
  variant={'sidebar'|'mobile'|'tabbed'}
  accessibilityLabel="Switch platform context"
/>
```

#### Sidebar Variant (Desktop)

```
┌─────────────────────────────────┐
│ YouAndINotAI                   │
├──────────────────

*[truncated — see source for full prompt]*