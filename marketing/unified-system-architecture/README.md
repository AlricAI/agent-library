# UNIFIED SYSTEM ARCHITECTURE

> **Last Updated**: September 9, 2025
**Version**: 2.0 - Integrated System

## Table of Contents

1. [System Overview](#system-overview)
2. [Core Compon

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas Unified System Architecture

**Last Updated**: September 9, 2025
**Version**: 2.0 - Integrated System

## Table of Contents

1. [System Overview](#system-overview)
2. [Core Components](#core-components)
3. [Integration Architecture](#integration-architecture)
4. [Data Flow](#data-flow)
5. [Service Communication](#service-communication)
6. [External Dependencies](#external-dependencies)
7. [Security Architecture](#security-architecture)
8. [Scalability and Performance](#scalability-and-performance)

## System Overview

Atlas is a comprehensive personal AI knowledge system that combines multiple processing pipelines into a unified cognitive amplification platform. The system integrates YouTube processing, PODEMOS ad-free podcast feeds, Mac Mini audio processing, and traditional content ingestion into a seamless experience.

### Key Architectural Principles

- **Single Model Architecture**: Gemini 2.5 Flash Lite for all AI processing
- **Unified Processing Queue**: All content processing through shared queue system
- **Graceful Degradation**: System operates with partial component failures
- **Distributed Processing**: Optional Mac Mini for dedicated audio processing
- **Real-time Integration**: Live feed monitoring and processing

## Core Components

### 1. Atlas Core Engine

**Location**: `/home/ubuntu/dev/atlas/`
**Purpose**: Central orchestration and data management

```
atlas/
├── unified_service_manager.py      # Central service controller
├── universal_processing_queue.py   # Unified task processing
├── helpers/
│   ├── database_config.py          # Centralized database access
│   ├── ai_interface.py             # AI processing abstraction
│   └── semantic_search_ranker.py   # Content search and ranking
```

**Key Features**:
- Centralized database configuration eliminates hardcoded paths
- Bulletproof process management prevents memory leaks
- Universal content extraction and processing
- Semantic search with 240,026+ indexed items

### 2. Content Proce

*[truncated — see source for full prompt]*