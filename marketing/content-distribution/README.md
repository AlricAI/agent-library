# CONTENT DISTRIBUTION

> This document provides detailed documentation for all content distribution tools available to the Content Distribution Manager agent.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Content Distribution Toolsets

This document provides detailed documentation for all content distribution tools available to the Content Distribution Manager agent.

## Tools Overview

| Tool Name           | Description                                          | Status |
| ------------------- | ---------------------------------------------------- | ------ |
| `publish_episode`   | Publish new episode to website and podcast platforms | Active |
| `update_tour_dates` | Update tour schedule on website                      | Active |
| `manage_cdn`        | Optimize CDN settings and cache invalidation         | Active |
| `seo_optimization`  | Optimize content for search engines                  | Active |

---

## publish_episode

Publishes new episodes to the website and podcast platforms.

### Parameters

| Parameter      | Type   | Required | Description                      |
| -------------- | ------ | -------- | -------------------------------- |
| `episode_data` | object | Yes      | Episode metadata and information |
| `audio_file`   | string | Yes      | Path to the audio file           |
| `video_file`   | string | No       | Path to the video file           |
| `show_notes`   | string | Yes      | Show notes and description       |

### Episode Data Structure

```json
{
  "title": "Episode Title",
  "episode_number": 42,
  "season": 3,
  "publish_date": "2024-01-15",
  "duration_minutes": 45,
  "guests": ["Guest Name"],
  "topics": ["Topic 1", "Topic 2"],
  "explicit": false
}
```

### Example Usage

```json
{
  "episode_data": {
    "title": "Best of 2023",
    "episode_number": 100,
    "season": 4,
    "publish_date": "2024-01-01",
    "duration_minutes": 60,
    "guests": ["Various"],
    "topics": ["year_review", "highlights"]
  },
  "audio_file": "/path/to/episode_100.mp3",
  "video_file": "/path/to/episode_100.mp4",
  "show_notes": "## Highlights\\n- Topic 1\\n- Topic 2"
}
```

### Output

Returns publish confirmation with:

- Episode URL
- RSS fee

*[truncated — see source for full prompt]*