# CAPTURE ARCHITECTURE

> ## Critical Problem Statement

**Current Issue**: Atlas currently conflates data capture with processing. When a user sends a URL, the system immediat

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Bulletproof Capture Architecture

## Critical Problem Statement

**Current Issue**: Atlas currently conflates data capture with processing. When a user sends a URL, the system immediately tries to fetch/parse/process it. If ANY step fails (network issues, parsing errors, disk space), the user's original input may be lost forever.

**Impact**: Users cannot trust the system with their valuable data because failure at any processing step means complete loss of input.

**Solution Required**: Two-stage architecture separating bulletproof capture (never fails) from processing (can fail safely and retry).

## Architecture Overview

### Current Flow (Problematic)
```
URL → immediate processing → success OR total failure
```

### Required Flow (Bulletproof)
```
URL → bulletproof capture (always succeeds) → processing queue → eventual processing
```

### Core Principles

1. **Capture Never Fails**: Capture functions must NEVER raise unhandled exceptions
2. **Atomic Operations**: Use atomic file operations (write to temp, then rename)
3. **Redundant Storage**: Create backup copies of all captured data immediately
4. **Comprehensive Logging**: Log everything with JSON format for easy LLM parsing
5. **Restartable Processing**: Make processing queue restartable and handle interruptions gracefully
6. **Preserve Originals**: Never modify captured items, only create processed versions

## Implementation Plan

### Priority 1: Bulletproof Capture Foundation

#### Create `ingest/capture/bulletproof_capture.py`

**Core Functions:**
```python
def capture_url(url: str, user_context: dict = None) -> dict:
    """NEVER FAILS. Immediately saves URL with metadata to multiple locations."""
    # Generate unique capture_id with timestamp
    # Save to primary + backup locations atomically
    # Return capture confirmation with tracking info

def capture_file(file_path: str, user_context: dict = None) -> dict:
    """NEVER FAILS. Immediately copies file to secure storage."""
    # Copy to prim

*[truncated — see source for full prompt]*