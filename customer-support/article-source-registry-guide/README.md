# ARTICLE SOURCE REGISTRY GUIDE

> ## 🚀 Overview

The new **Article Source Registry** solves the critical problem of service outages like the 12ft.io shutdown in July 2025. It provides

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Article Source Registry Guide

## 🚀 Overview

The new **Article Source Registry** solves the critical problem of service outages like the 12ft.io shutdown in July 2025. It provides a centralized, configurable system for managing article fetching sources with automatic failover capabilities.

## 📋 What This Solves

### OLD Problems (Fixed)
- ❌ **12ft.io Shutdown**: When 12ft.io went down, manual code changes were required
- ❌ **Hardcoded Strategies**: Sources hardcoded in `article_manager.py`
- ❌ **No Failover**: Single point of failure for each source type
- ❌ **Manual Priority Management**: No automatic priority adjustment
- ❌ **No Health Monitoring**: No way to detect service outages automatically

### NEW Solutions
- ✅ **Automatic Outage Detection**: Health checks for all services
- ✅ **Dynamic Failover**: Automatically promotes alternatives when services fail
- ✅ **Centralized Configuration**: JSON-based source management
- ✅ **Performance Tracking**: Automatic success rate monitoring and priority adjustment
- ✅ **Easy Source Addition**: Add new services without code changes

## 🏗️ System Architecture

### Core Components

1. **`helpers/article_source_registry.py`** - Main registry system
2. **`helpers/enhanced_article_manager.py`** - Enhanced manager using registry
3. **`config/article_sources.json`** - Source configurations

### Source Configuration Format

```json
{
  "name": "paywall_bypass",
  "display_name": "Paywall Bypass Services",
  "description": "Multiple paywall bypass services (12ft.io alternatives)",
  "source_type": "paywall_bypass",
  "url_patterns": [".*"],
  "content_patterns": ["subscribe", "premium", "sign in"],
  "strategy_class": "helpers.article_strategies.PaywallBypassStrategy",
  "enabled": true,
  "priority": 900,
  "success_rate": 0.60,
  "timeout_seconds": 25,
  "rate_limit_delay": 3.0,
  "auto_disable": true,
  "health_check_url": ""
}
```

## 🔄 Outage Handling Demo

### Before (12ft.io Shutdown)
```python
# PROBLEM: Manual in

*[truncated — see source for full prompt]*