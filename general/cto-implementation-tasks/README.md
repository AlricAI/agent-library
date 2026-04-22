# Cto Implementation Tasks

> ## Overview

This document outlines specific implementation tasks for the CTO (b02a21c7-737e-4177-91ac-6d8e57805801) based on completed UX design work

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CTO Implementation Tasks for YouAndINotAI

## Overview

This document outlines specific implementation tasks for the CTO (b02a21c7-737e-4177-91ac-6d8e57805801) based on completed UX design work. These tasks focus on Priority 1 essential updates that are critical for platform functionality and user safety.

## Task 1: Enhanced Safety Drawer Implementation

**Component**: SafetyDrawer
**Files**: `design-specs/safety-features-enhancement.md`
**Implementation Handoff**: `development/safety-features-handoff.md`

### Requirements:

- Add mute user functionality with 24-hour default duration
- Add restrict profile visibility option with granular controls
- Improve report form with better context gathering including evidence attachment
- Add safety status indicators on profiles and messages
- Optimize for mobile access with thumb-friendly controls

### API Endpoints Needed:

- POST /api/safety/mute - User muting with duration controls
- POST /api/safety/restrict - Profile visibility restrictions
- POST /api/report - Enhanced reporting with evidence and context
- GET /api/safety/status/{userId} - Safety status indicators

### Technical Considerations:

- Implement websocket connections for real-time safety notifications
- Ensure offline queue management for safety actions
- Add proper error handling and retry mechanisms
- Implement audit logging for all safety-related actions

## Task 2: Improved Event Cards with Imagery Support

**Component**: EventDiscoveryCard
**Files**: `design-specs/real-world-meetups-enhancement.md`
**Implementation Handoff**: `development/community-features-handoff.md`

### Requirements:

- Add event imagery support with responsive image handling
- Include weather considerations with integration to weather API
- Show friend attendance indicators with avatar display
- Add accessibility information for venue accessibility
- Include estimated cost/category tags with visual indicators

### API Endpoints Needed:

- GET /api/events/{id}/image - Event imag

*[truncated — see source for full prompt]*