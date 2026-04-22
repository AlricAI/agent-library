# WEBSOCKET API IMPLEMENTATION

> This document describes the implementation of WebSocket support and Conversion REST API endpoints for the ModPorter-AI backend.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# WebSocket and Conversion API Implementation

This document describes the implementation of WebSocket support and Conversion REST API endpoints for the ModPorter-AI backend.

## Overview

This implementation adds:
- **WebSocket server** for real-time conversion progress updates
- **REST API endpoints** for managing conversion jobs
- **Integration** with existing conversion workflow

## Architecture

### Components

1. **WebSocket Manager** (`websocket/manager.py`)
   - Manages active WebSocket connections
   - Supports multiple concurrent clients per conversion
   - Handles connection lifecycle (connect/disconnect)
   - Broadcasts messages to connected clients

2. **Progress Handler** (`websocket/progress_handler.py`)
   - Defines message schemas for progress updates
   - Provides helper methods for broadcasting agent status
   - Handles conversion completion/failure notifications

3. **Conversion API** (`api/conversions.py`)
   - REST endpoints for conversion management
   - WebSocket endpoint for real-time progress
   - File upload validation and processing
   - Integration with database and cache

### Message Flow

```
Client                    Backend                    AI Engine
  |                          |                            |
  |-- POST /conversions ---->|                            |
  |                          |-- Create job in DB -------->|
  |<-- 202 Accepted ---------|                            |
  |                          |                            |
  |-- WS connect ----------->|                            |
  |<-- Connection confirmed -|                            |
  |                          |                            |
  |                          |-- Start conversion -------->|
  |                          |                            |
  |<-- Agent: JavaAnalyzer --|                            |
  |     (0-25%)              |                            |
  |                          |                            |
  |<-- Agent: 

*[truncated — see source for full prompt]*