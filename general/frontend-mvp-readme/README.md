# FRONTEND MVP README

> This document describes the complete frontend MVP implementation for ModPorter AI's upload-to-download flow.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Frontend MVP Implementation

This document describes the complete frontend MVP implementation for ModPorter AI's upload-to-download flow.

## Overview

The MVP provides a complete user flow from uploading a Java mod to downloading the converted Bedrock add-on, with real-time progress tracking and detailed reporting.

## Architecture

### Core Components

1. **ConversionFlowManager** (`/components/ConversionFlow/`)
   - Orchestrates the complete upload-to-download experience
   - Manages state transitions: idle → uploading → converting → completed/failed
   - Handles error recovery and retry logic
   - Provides auto-reset functionality

2. **ConversionUploadEnhanced** (`/components/ConversionUpload/ConversionUploadEnhanced.tsx`)
   - Enhanced upload component with drag-drop support
   - File validation (type, size)
   - URL input for CurseForge/Modrinth links
   - Smart Assumptions and Dependencies options
   - Real-time upload progress indication

3. **ConversionProgress** (`/components/ConversionProgress/`)
   - Real-time progress tracking via WebSocket
   - Fallback polling when WebSocket unavailable
   - Visual progress bar with percentage
   - Agent status display
   - Estimated time remaining

4. **ConversionReportContainer** (`/components/ConversionReport/`)
   - Fetches and displays conversion results
   - Shows Smart Assumptions applied
   - Displays feature analysis and developer logs
   - Provides download link for .mcaddon file

### Services

1. **WebSocket Service** (`/services/websocket.ts`)
   - Real-time bidirectional communication
   - Automatic reconnection with exponential backoff
   - Graceful fallback to HTTP polling
   - Connection status tracking

2. **API Service** (`/services/api.ts`)
   - All backend communication
   - File upload, conversion initiation
   - Status polling, result download
   - Error handling with detailed messages

## User Flow

```
1. User arrives on ConvertPage (/)
   ↓
2. Drag-drop JAR file or paste URL
   ↓
3. Configu

*[truncated — see source for full prompt]*