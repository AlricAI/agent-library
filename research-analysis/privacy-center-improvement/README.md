# Privacy Center Improvement

> ## Overview

Enhance the privacy center to provide users with greater control, transparency, and understanding of their data while maintaining complia

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Design Specification: Privacy Center Improvement

## Overview

Enhance the privacy center to provide users with greater control, transparency, and understanding of their data while maintaining compliance with legal requirements.

## Current State Analysis

The current DataPrivacyDashboard provides essential privacy controls but lacks:

- Visual data mapping
- Clear explanation of data lifecycle
- Granular control options
- Impact visualization
- Mobile-optimized interface

## Design Goals

1. **Transparency First** - Clear visibility into what data is collected and why
2. **Granular Control** - Detailed options for managing different data types
3. **Educational Experience** - Help users understand privacy implications
4. **Simple Actions** - Straightforward paths for common privacy tasks
5. **Mobile Optimization** - Easy access and management on all devices

## Proposed Enhancements

### 1. Enhanced Privacy Dashboard Interface

```
┌─────────────────────────────────────┐
│  Privacy Center             [Help]  │
├─────────────────────────────────────┤
│                                     │
│  Your Data Snapshot                │
│  ┌─────────────────────────────┐   │
│  │ Profile: 95% Complete       │   │
│  │ [Progress Visualization]    │   │
│  │ Last Updated: Today         │   │
│  └─────────────────────────────┘   │
│                                     │
│  Data Categories                   │
│  ┌─────────────────────────────┐   │
│  │ Profile Information         │   │
│  │ ☑ Photos (12)               │   │
│  │ ☑ Bio & Interests           │   │
│  │ ☐ Location History          │   │
│  │ ▼ Show Details              │   │
│  └─────────────────────────────┘   │
│                                     │
└─────────────────────────────────────┘
```

### 2. Data Lifecycle Visualization

- Collection points mapping
- Retention period indicators
- Processing purpose explanations
- Third-party sharing disclosures
- Deletion timeline visualization

### 3. Granular Privacy

*[truncated — see source for full prompt]*