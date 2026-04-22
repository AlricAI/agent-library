# Podemos System Integration

> ## Overview

The PODEMOS Personal Podcast Feed System is now fully integrated with the Atlas infrastructure, providing:

- **Real-time Feed Monitoring

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PODEMOS System Integration Documentation

## Overview

The PODEMOS Personal Podcast Feed System is now fully integrated with the Atlas infrastructure, providing:

- **Real-time Feed Monitoring**: 1-2 minute polling of 191 podcast feeds
- **Ultra-Fast Processing**: 19-minute target from episode release to clean feed
- **Private RSS Hosting**: Authenticated access to ad-free feeds on Oracle OCI
- **Atlas Integration**: Shared processing queue and resource management

## System Architecture

```
┌─────────────────────┐    ┌──────────────────────┐    ┌─────────────────────┐
│   Feed Monitor      │────│   Atlas Processing  │────│   RSS Feed Server   │
│   (podemos_feed_    │    │   Queue (shared)     │    │   (Oracle OCI)      │
│    monitor.py)      │    │                      │    │                      │
└─────────────────────┘    └──────────────────────┘    └─────────────────────┘
           │                           │                           │
           │                           │                           │
           ▼                           ▼                           ▼
┌─────────────────────┐    ┌──────────────────────┐    ┌─────────────────────┐
│  OPML Import        │    │  Mac Mini            │    │  Private Feeds      │
│  (191 feeds)        │    │  Transcription       │    │  (Authenticated)    │
└─────────────────────┘    └──────────────────────┘    └─────────────────────┘
```

## Key Components

### 1. Feed Monitoring (`podemos_feed_monitor.py`)
- **OPML Import**: Loads 191 podcast feeds from Overcast export
- **Real-time Polling**: 1-2 minute intervals for new episodes
- **Immediate Triggering**: Downloads detected within seconds
- **Atlas Queue Integration**: Episodes added to shared processing queue

### 2. Ultra-Fast Processing (`podemos_ultra_fast_processor.py`)
- **whisper.cpp Integration**: Fast transcription (~7 minutes)
- **Multi-Method Ad Detection**: Keywords, silence, timing patterns
- **FFmpeg Audio Cutting**: Removes detected ad 

*[truncated — see source for full prompt]*