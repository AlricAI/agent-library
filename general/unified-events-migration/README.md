# UNIFIED EVENTS MIGRATION

> ## Overview
The unified event system standardizes workflow event payloads across activity history, in-app notification wiring, and related messaging s

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Unified Events Migration Guide

## Overview
The unified event system standardizes workflow event payloads across activity history, in-app notification wiring, and related messaging surfaces.

Primary source files:
- `src/lib/unified-events.ts`
- `src/lib/emit-event.ts`

## Current behavior (important)
- `emitEvent()` validates the event and records activity through `/api/events/record-activity`.
- `emitEvent()` does **not** directly enqueue client notification UI state.
- For UI notification delivery, convert events with `getNotificationFromEvent()` and send through `pushNotification()`.
- Workflow Slack delivery remains centralized in `emitWorkflowSlackEvent()` and is triggered by workflow API routes.

## Canonical unified event types
The current `UnifiedEventType` union is:
- `blog_writer_status_changed`
- `blog_publisher_status_changed`
- `blog_writer_assigned`
- `blog_publisher_assigned`
- `blog_awaiting_writer_action`
- `blog_awaiting_publisher_action`
- `blog_publish_overdue`
- `social_post_status_changed`
- `social_post_assigned`
- `social_post_reassigned`
- `social_post_awaiting_action`
- `social_post_editor_assigned`
- `social_review_overdue`
- `social_publish_overdue`
- `social_post_live_link_reminder`

## Notification mapping snapshot
- Status changes → `stage_changed`
- Assignment events (`*_assigned`) → `task_assigned`
- Reassignment (`social_post_reassigned`) → `assignment_changed`
- Awaiting/overdue/reminder events → `awaiting_action`

Mapping source: `UNIFIED_EVENT_TO_NOTIFICATION_TYPE` in `src/lib/unified-events.ts`.

## Required event payload fields
Minimum required:
- `type`
- `contentType` (`blog` or `social_post`)
- `contentId`
- `actor` (user id)

Common optional fields:
- `oldValue`
- `newValue`
- `fieldName`
- `actorName`
- `targetUserId`
- `targetUserName`
- `targetUserNames`
- `contentTitle`
- `metadata`
- `timestamp` (number; use `Date.now()`)

## Migration pattern
1. Replace ad-hoc event-like objects with a typed `UnifiedEvent`.
2. Emit

*[truncated — see source for full prompt]*