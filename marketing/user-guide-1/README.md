# USER GUIDE

> ## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Typical Workflows](#typical-workflows)
4. [Tool Over

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Podcast Production Toolset - User Guide

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Typical Workflows](#typical-workflows)
4. [Tool Overview](#tool-overview)
5. [Best Practices](#best-practices)
6. [Troubleshooting](#troubleshooting)

---

## Introduction

The Podcast Production Toolset provides three powerful tools for automating podcast production workflows:

- **Video Analysis Tool**: Analyze video footage for speaker detection and optimal editing
- **Audio Processing Tool**: Clean, enhance, and master audio for distribution
- **Content Scheduling Tool**: Schedule and manage multi-platform social media posts

These tools are designed to work together to streamline your podcast production from recording to distribution.

---

## Getting Started

### Prerequisites

Before using the tools, ensure you have:

1. **Python 3.10 or higher** installed
2. **FFmpeg** installed (for video and audio tools)
   ```bash
   # Ubuntu/Debian
   sudo apt-get install ffmpeg
   
   # macOS
   brew install ffmpeg
   ```
3. The toolset package installed in your Python environment

### Installation

```bash
# Navigate to the repository
cd /path/to/cloudcurio-monorepo-new

# Install the package
pip install -e .
```

### Basic Setup

```python
from agents.toolsets.jcsnotfunny import (
    VideoAnalysisTool,
    AudioProcessingTool,
    ContentSchedulingTool
)

# Initialize tools
video_tool = VideoAnalysisTool()
audio_tool = AudioProcessingTool()
scheduling_tool = ContentSchedulingTool()
```

---

## Typical Workflows

### Workflow 1: Complete Episode Production

This workflow takes you from raw footage to published content.

```python
from datetime import datetime, timedelta

# Step 1: Analyze raw video
print("Step 1: Analyzing video...")
video_analysis = video_tool.execute(
    video_path='/path/to/raw_footage.mp4',
    analysis_type='full'
)

print(f"✓ Detected {video_analysis['speaker_detection']['speakers_detected']} speakers")
p

*[truncated — see source for full prompt]*