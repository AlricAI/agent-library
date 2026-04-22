# Connection Components

> ## Overview

A comprehensive system for managing social connections on YouAndINotAI, enabling users to find, connect with, and maintain relationships 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Connection Components Specification

## Overview

A comprehensive system for managing social connections on YouAndINotAI, enabling users to find, connect with, and maintain relationships with like-minded community members focused on genuine connection rather than dating.

## Component Structure

### ConnectionManager

Primary container for connection-related functionality

### ConnectionCard

Individual display of a user connection with key information

### ConnectionRequest

Interface for managing incoming connection requests

### ConnectionFinder

Tools for discovering potential connections

### ConnectionGroups

Interface for managing connection groups/clusters

### MutualConnections

Display of shared connections between users

## Component Specifications

### ConnectionManager

#### Props

| Prop                    | Type                     | Required | Description                           |
| ----------------------- | ------------------------ | -------- | ------------------------------------- |
| connections             | Array<Connection>        | Yes      | Array of connection objects           |
| connectionRequests      | Array<ConnectionRequest> | Yes      | Incoming connection requests          |
| currentUser             | User                     | Yes      | Currently logged in user              |
| onViewProfile           | Function                 | Yes      | Callback when user views a profile    |
| onAcceptRequest         | Function                 | Yes      | Callback to accept connection request |
| onRejectRequest         | Function                 | Yes      | Callback to reject connection request |
| onSendMessage           | Function                 | Yes      | Callback to initiate message          |
| onViewMutualConnections | Function                 | No       | Callback to view mutual connections   |

#### Connection Interface

```typescript
interface Connection {
  id: string;
  user: User;
  connectedAt: Date;
  relationshipType

*[truncated — see source for full prompt]*