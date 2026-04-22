# TECHNICAL GUIDE

> This document provides detailed technical information about the implementation of the web scraping workflow, including node configurations, data structures, and advanced customization options.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Technical Implementation Guide: Web Scraping Workflow

This document provides detailed technical information about the implementation of the web scraping workflow, including node configurations, data structures, and advanced customization options.

## Architecture Overview

The workflow follows a modular architecture with three distinct components that can be used independently or combined:

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│                 │     │                 │     │                 │
│  Split Items    │────▶│  Data Scraping  │────▶│   Pagination    │
│                 │     │                 │     │                 │
└─────────────────┘     └─────────────────┘     └─────────────────┘
```

## Node Configurations

### HTTP Request Node

```javascript
{
  "parameters": {
    "url": "={{$json.url}}",
    "authentication": "none",
    "method": "GET",
    "sendQuery": true,
    "sendBody": false,
    "options": {
      "timeout": 10000,
      "responseFormat": "json"
    }
  }
}
```

**Key Configuration Points:**
- Dynamic URL from workflow data
- 10-second timeout to handle slow responses
- JSON response format expected

### HTML Extract Node

```javascript
{
  "parameters": {
    "extractionValues": {
      "values": [
        {
          "key": "articleTitle",
          "cssSelector": "h1#firstHeading",
          "returnArray": false
        },
        {
          "key": "content",
          "cssSelector": "div#mw-content-text",
          "returnArray": false
        }
      ]
    }
  }
}
```

**Advanced Selector Techniques:**
- Use `@attr` to extract specific attributes (e.g., `img@src`)
- Use `:nth-child(n)` for selecting specific elements in a list
- Combine selectors for more precise targeting

### Pagination Implementation

The pagination logic uses a combination of:
1. Counter initialization
2. Dynamic URL construction
3. Conditional checking
4. Counter incrementing
5. Loop back mechanism

## Data Structures

### I

*[truncated — see source for full prompt]*