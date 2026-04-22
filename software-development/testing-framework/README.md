# TESTING FRAMEWORK

> ## Overview

Atlas now includes a comprehensive automated testing framework that validates all functionality systematically, eliminating the need for 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🧪 Atlas Testing Framework

## Overview

Atlas now includes a comprehensive automated testing framework that validates all functionality systematically, eliminating the need for manual "check this, test this" requests.

## 🚀 Quick Start

```bash
# Run core functionality tests
python3 -m pytest tests/test_web_endpoints.py tests/test_cognitive_features.py -v

# Run all tests (excluding broken legacy tests)
python3 -m pytest tests/test_web_endpoints.py tests/test_cognitive_features.py tests/test_e2e.py -v

# Run with coverage
python3 -m pytest tests/test_web_endpoints.py --cov=web --cov=ask
```

## 🎯 What Gets Tested

### ✅ Web Interface (test_web_endpoints.py)
- **Mobile Dashboard**: All cognitive features load without crashes
- **Search & Filters**: Date, type, source filtering with state persistence
- **Content Management APIs**: Delete, tag, archive endpoints function
- **Responsive Design**: Mobile-first layout and touch optimization
- **API Endpoints**: JSON responses for all cognitive features

### ✅ Cognitive Features (test_cognitive_features.py)
- **Initialization**: All 6 cognitive engines start without errors
- **Data Returns**: Proper structured data from each feature
- **Web Compatibility**: Formats work with template expectations
- **MetadataManager Integration**: Config loading and database access

### ✅ End-to-End Workflows (test_e2e.py)
- **Complete User Journeys**: Mobile workflows from start to finish
- **API Integration**: Full request/response cycles
- **Database Operations**: Content CRUD with proper schema
- **System Integration**: All imports and configurations work

## 🤖 Continuous Integration

### GitHub Actions (.github/workflows/test.yml)

**Automated Testing**:
- **Triggers**: Every push, PR, and daily at 2 AM UTC
- **Matrix Testing**: Python 3.9, 3.10, 3.11 compatibility
- **Test Categories**: Unit, integration, end-to-end, security
- **Coverage Reports**: Automatic coverage tracking with Codecov

**Security Scanning**:
- **Bandit**: 

*[truncated — see source for full prompt]*