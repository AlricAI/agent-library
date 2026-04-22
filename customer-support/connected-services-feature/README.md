# Connected Services Feature

> ## Overview
The Connected Services feature allows users to manage third-party OAuth connections (Google and Slack) from the Settings page. Users can s

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Connected Services Feature

## Overview
The Connected Services feature allows users to manage third-party OAuth connections (Google and Slack) from the Settings page. Users can see connection status, connection date, and disconnect services. This feature integrates seamlessly with the existing OAuth sign-in flow and notification preferences.

## Architecture

### Database Schema
**Table: `user_integrations`**
- Tracks which OAuth services are connected per user
- Auto-populated when new users are created
- RLS policies enforce user self-access and admin audit access

```sql
user_id (FK to auth.users)
google_connected (BOOLEAN, default: FALSE)
google_connected_at (TIMESTAMP, nullable)
slack_connected (BOOLEAN, default: FALSE)
slack_connected_at (TIMESTAMP, nullable)
created_at, updated_at (TIMESTAMP)
```

### API Endpoints

#### `GET /api/users/integrations`
Fetch current user's connected services status.

**Authorization**: Bearer token required

**Response**:
```json
{
  "google_connected": false,
  "google_connected_at": null,
  "slack_connected": true,
  "slack_connected_at": "2026-03-21T18:39:01Z"
}
```

#### `PATCH /api/users/integrations`
Update integration connection status. Called when user connects/disconnects a service.

**Authorization**: Bearer token required

**Body**:
```json
{
  "google_connected": true,
  "slack_connected": false
}
```

**Behavior**:
- Setting `google_connected: true` automatically sets `google_connected_at` to current timestamp
- Setting to `false` clears the connection but keeps historical `connected_at` for audit
- Creates row if doesn't exist (handled by migration auto-population)

### Frontend Components

#### `ConnectedServicesForm` (`src/components/connected-services-form.tsx`)
Main UI component for managing connected services.

**Features**:
- Displays Google and Slack with icon/status badges
- Shows "Connected" (green badge) or "Not connected" (grey badge)
- Shows connection date for connected services
- Disconnect button 

*[truncated — see source for full prompt]*