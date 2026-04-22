# Smart Transcription Pipeline

> ## Overview

The Smart Transcription Pipeline is an intelligent podcast transcription system that processes 37 prioritized podcasts according to speci

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Smart Transcription Pipeline with Mac Mini Processing

## Overview

The Smart Transcription Pipeline is an intelligent podcast transcription system that processes 37 prioritized podcasts according to specific configuration requirements. It implements efficient transcript discovery, selective audio processing, and Mac Mini local transcription capabilities.

## Key Features

### ✅ **Completed Implementation**

1. **Intelligent Transcript Discovery**
   - ✅ Checks `Transcript_Only` flag per podcast from `prioritized.csv`
   - ✅ Searches for existing transcripts first before any audio processing
   - ✅ Only downloads audio if transcript unavailable AND needed
   - ✅ Respects exact episode counts from prioritized configuration

2. **Mac Mini Local Processing**
   - ✅ SSH-based remote transcription using Whisper large-v3 model
   - ✅ Configurable concurrent job processing
   - ✅ Automatic audio cleanup and error handling
   - ✅ 30-minute timeout protection

3. **Universal Processing Queue**
   - ✅ Single queue system prevents competing parallel processes
   - ✅ Priority-based job scheduling
   - ✅ Status tracking and retry mechanisms
   - ✅ SQLite-based queue persistence

4. **Prioritized Configuration**
   - ✅ Loads 35 podcasts from `config/podcasts_prioritized.csv`
   - ✅ Handles transcript-only vs full processing modes
   - ✅ Respects episode count limits per podcast
   - ✅ Excludes marked podcasts automatically

## Usage

### Command Line Interface

```bash
# Show all prioritized podcasts configuration
python3 smart_transcription.py --show-config

# Process all prioritized podcasts
python3 smart_transcription.py --process-all

# Process specific podcasts
python3 smart_transcription.py --process-podcasts "Acquired" "99% Invisible"

# Process Mac Mini transcription queue
python3 smart_transcription.py --process-queue

# Show processing status and statistics
python3 smart_transcription.py --status

# Dry run mode (show what would be processed)
python3 smart_transcripti

*[truncated — see source for full prompt]*