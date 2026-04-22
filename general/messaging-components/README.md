# Messaging Components

> ## Overview

A comprehensive set of components for enabling secure, accessible, and trust-building communication between community members on YouAndIN

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Messaging Components Specification

## Overview

A comprehensive set of components for enabling secure, accessible, and trust-building communication between community members on YouAndINotAI. These components facilitate genuine connections while maintaining user safety and privacy.

## Component Structure

### MessageThread

Primary container for a conversation between users

### MessageBubble

Individual message display with sender information and content

### MessageInput

Input area for composing and sending messages

### ConversationList

Sidebar or list view of active conversations

### TypingIndicator

Visual indicator showing when contacts are typing

### MessageActions

Dropdown or context menu for message actions (reply, report, etc.)

## Component Specifications

### MessageThread

#### Props

| Prop          | Type           | Required | Description                             |
| ------------- | -------------- | -------- | --------------------------------------- |
| messages      | Array<Message> | Yes      | Array of message objects                |
| participants  | Array<User>    | Yes      | Users in the conversation               |
| currentUser   | User           | Yes      | Currently logged in user                |
| onSendMessage | Function       | Yes      | Callback when user sends a message      |
| onLoadMore    | Function       | No       | Callback to load earlier messages       |
| isLoading     | Boolean        | No       | Whether loading older messages          |
| hasMore       | Boolean        | No       | Whether there are more messages to load |

#### Message Interface

```typescript
interface Message {
  id: string;
  content: string;
  senderId: string;
  timestamp: Date;
  status: 'sent' | 'delivered' | 'read';
  attachments?: Array<Attachment>;
  reactions?: Array<Reaction>;
}

interface Attachment {
  id: string;
  type: 'image' | 'document' | 'link';
  url: string;
  name?: string;
  size?: number;
}

interface Reaction {
 

*[truncated — see source for full prompt]*