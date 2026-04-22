# API DOCUMENTATION

> ## Overview

The Atlas API provides a unified interface for all cognitive amplification features, content management, and system analytics. It combine

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas API Documentation

## Overview

The Atlas API provides a unified interface for all cognitive amplification features, content management, and system analytics. It combines both new FastAPI-based endpoints and existing Flask-based services.

## API Structure

### New FastAPI Endpoints

1. **Authentication API** (`/api/v1/auth/*`)
   - User registration and login
   - API key management
   - JWT token authentication

2. **Content Management API** (`/api/v1/content/*`)
   - List, create, update, and delete content items
   - Content processing and reprocessing
   - Content statistics and health checks

3. **Cognitive Features API** (`/api/v1/cognitive/*`)
   - Proactive content surfacing
   - Temporal relationship analysis
   - Socratic question generation
   - Spaced repetition recall
   - Pattern detection and insights

4. **Transcript Search API** (`/api/v1/transcripts/*`)
   - Advanced transcript search and discovery
   - Podcast transcript filtering and analytics
   - Speaker-based content filtering
   - Modern web interface for transcript exploration

5. **Transcription Processing API** (`/api/v1/transcriptions/*`)
   - Mac Mini transcription result submission
   - External transcription service integration
   - Transcription status tracking and management

6. **Worker Management API** (`/api/v1/worker/*`)
   - Mac Mini worker task coordination
   - Background processing queue management
   - Distributed task status monitoring

7. **Podcast Progress API** (`/api/v1/podcast-progress/*`)
   - PODEMOS processing status tracking
   - Episode processing progress monitoring
   - Feed update notifications and alerts

8. **Apple Shortcuts API** (`/api/v1/shortcuts/*`)
   - iOS/macOS shortcut integration endpoints
   - Voice capture and content submission
   - Mobile device content processing

### Existing Flask Endpoints

1. **Analytics API** (`/api/analytics/*`)
   - System metrics
   - Content processing statistics
   - User engagement analytics
   - Dashboard d

*[truncated — see source for full prompt]*