# PODCAST SOURCE REGISTRY GUIDE

> ## 🚀 Overview

The new **Podcast Sources Registry** replaces hardcoded podcast detection logic with a flexible, configurable system that makes it eas

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Podcast Sources Registry Guide

## 🚀 Overview

The new **Podcast Sources Registry** replaces hardcoded podcast detection logic with a flexible, configurable system that makes it easy to add new transcript sources.

## 📋 What This Solves

### OLD Problems (Fixed)
- ❌ Hardcoded podcast names in `_is_atp_episode()`, `_is_tal_episode()`, etc.
- ❌ Difficult to add new podcast sources
- ❌ No source performance tracking
- ❌ Manual priority management
- ❌ No centralized configuration

### NEW Solutions
- ✅ **Centralized Registry**: All sources in `config/podcast_sources.json`
- ✅ **Easy Addition**: Add new sources without code changes
- ✅ **Performance Tracking**: Automatic success rate monitoring
- ✅ **Priority Management**: Configurable priority system
- ✅ **Pattern Matching**: Flexible URL and title pattern matching

## 🏗️ System Architecture

### Core Components

1. **`helpers/podcast_source_registry.py`** - Main registry system
2. **`helpers/enhanced_transcript_lookup.py`** - Enhanced lookup using registry
3. **`config/podcast_sources.json`** - Source configurations

### Source Configuration Format

```json
{
  "name": "atp",
  "display_name": "Accidental Tech Podcast",
  "description": "ATP episodes from catatp.fm",
  "url_patterns": ["atp\\.fm", "accidental.*tech", "atp"],
  "title_patterns": ["\\d+:", "Episode \\d+", "ATP \\d+"],
  "scraper_class": "helpers.atp_transcript_scraper.ATPTranscriptScraper",
  "enabled": true,
  "priority": 100,
  "requires_auth": false,
  "success_rate": 0.85
}
```

## 🔄 Migration Guide

### For Developers

#### OLD Way (Hardcoded)
```python
# PROBLEM: Hardcoded logic
def _is_atp_episode(self, podcast_name: str, episode_title: str) -> bool:
    atp_indicators = ['accidental tech podcast', 'atp.fm', 'atp']
    combined_text = f"{podcast_name} {episode_title}".lower()
    return any(indicator in combined_text for indicator in atp_indicators)
```

#### NEW Way (Registry-based)
```python
# SOLUTION: Use registry
from helpers.podcast_so

*[truncated — see source for full prompt]*