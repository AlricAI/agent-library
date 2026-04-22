# Notification Components

> ## Overview

A comprehensive notification system for YouAndINotAI that keeps users informed about community activities, messages, events, and platform

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Notification Components Specification

## Overview

A comprehensive notification system for YouAndINotAI that keeps users informed about community activities, messages, events, and platform updates while respecting their preferences and attention.

## Component Structure

### Notification Center

Primary container for displaying and managing notifications

### NotificationItem

Individual notification display with action buttons

### NotificationBadge

Visual indicator for unread notifications

### NotificationPreferences

Settings interface for notification controls

### PushNotificationHandler

System for handling push notifications

## Component Specifications

### Notification Center

#### Props

| Prop                | Type                | Required | Description                           |
| ------------------- | ------------------- | -------- | ------------------------------------- |
| notifications       | Array<Notification> | Yes      | Array of notification objects         |
| currentUser         | User                | Yes      | Currently logged in user              |
| onNotificationClick | Function            | Yes      | Callback when notification is clicked |
| onMarkAsRead        | Function            | Yes      | Callback to mark notification as read |
| onDismiss           | Function            | Yes      | Callback to dismiss notification      |
| onClearAll          | Function            | No       | Callback to clear all notifications   |

#### Notification Interface

```typescript
interface Notification {
  id: string;
  type: 'message' | 'event' | 'connection' | 'system' | 'reminder';
  title: string;
  content: string;
  timestamp: Date;
  isRead: boolean;
  isDismissed: boolean;
  priority: 'low' | 'medium' | 'high';
  actions?: Array<NotificationAction>;
  relatedEntity?: {
    type: string;
    id: string;
  };
}

interface NotificationAction {
  label: string;
  action: string;
  primary: boolean;
}
```

#### Behavior

- Sort notifica

*[truncated — see source for full prompt]*