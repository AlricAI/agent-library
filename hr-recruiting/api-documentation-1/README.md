# API DOCUMENTATION

> This document provides comprehensive API documentation for the three core podcast production tools.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Core Tools API Documentation

This document provides comprehensive API documentation for the three core podcast production tools.

## Table of Contents

1. [Video Analysis Tool](#video-analysis-tool)
2. [Audio Processing Tool](#audio-processing-tool)
3. [Content Scheduling Tool](#content-scheduling-tool)

---

## Video Analysis Tool

### Overview

The VideoAnalysisTool provides comprehensive video analysis capabilities for podcast production, including speaker detection, engagement scoring, optimal cut points identification, and scene segmentation.

### Installation & Setup

```python
from agents.toolsets.jcsnotfunny import VideoAnalysisTool

# Basic initialization
tool = VideoAnalysisTool()

# With custom configuration
config = {
    'ffmpeg_path': '/usr/bin/ffmpeg',
    'ffprobe_path': '/usr/bin/ffprobe',
    'temp_dir': '/custom/temp',
    'max_file_size_mb': 3000,
    'supported_formats': ['mp4', 'mov', 'avi']
}
tool = VideoAnalysisTool(config=config)
```

### Configuration Options

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ffmpeg_path` | str | 'ffmpeg' | Path to ffmpeg binary |
| `ffprobe_path` | str | 'ffprobe' | Path to ffprobe binary |
| `temp_dir` | str | '/tmp/video_analysis' | Temporary directory for analysis |
| `max_file_size_mb` | int | 5000 | Maximum file size in MB |
| `supported_formats` | list | ['mp4', 'mov', 'avi', 'mkv'] | Supported video formats |

### Methods

#### execute(video_path, analysis_type='full', **kwargs)

Execute video analysis on the specified file.

**Parameters:**
- `video_path` (str, required): Path to the video file to analyze
- `analysis_type` (str, optional): Type of analysis to perform
  - `'quick'`: Basic metadata and technical analysis
  - `'full'`: Complete analysis with all features (default)
  - `'speaker'`: Focus on speaker detection
  - `'cuts'`: Focus on optimal cut points
- `**kwargs`: Additional analysis parameters

**Returns:**
Dict containing analysis results:

*[truncated — see source for full prompt]*