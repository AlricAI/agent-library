# User Profile Component

> ## Component Name

UserProfile

## Overview

A comprehensive user profile component that showcases authentic community members while prioritizing priv

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# UserProfile Component Specification

## Component Name

UserProfile

## Overview

A comprehensive user profile component that showcases authentic community members while prioritizing privacy, safety, and genuine connection. Designed for YouAndINotAI's mission of fostering real-world community connections rather than romantic relationships.

## Props/State

### Props

| Prop          | Type                             | Required | Description                                                 |
| ------------- | -------------------------------- | -------- | ----------------------------------------------------------- |
| user          | UserProfileData                  | Yes      | User profile data object                                    |
| currentUser   | boolean                          | No       | Whether this is the current user's profile (default: false) |
| onEdit        | function                         | No       | Callback when user initiates edit mode                      |
| onViewEvents  | function                         | No       | Callback to view user's upcoming events                     |
| onSendMessage | function                         | No       | Callback to initiate messaging (for connections only)       |
| onReportUser  | function                         | No       | Callback to report user                                     |
| onBlockUser   | function                         | No       | Callback to block user                                      |
| variant       | 'full' \| 'compact' \| 'preview' | No       | Display variant (default: 'full')                           |

### UserProfileData Interface

```typescript
interface UserProfileData {
  id: string;
  name: string;
  username: string;
  avatarUrl: string;
  joinDate: Date;
  location?: {
    city: string;
    state: string;
  };
  bio?: string;
  interests: Array<{
    id: string;
    name: string;
    category: 'hobby' | 'cause' | 'skill' | 'topic';
  }>;
  communityRoles: 

*[truncated — see source for full prompt]*