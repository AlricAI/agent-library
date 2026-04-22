# API COMPREHENSIVE

> ## 🚀 Overview

ModPorter AI provides a RESTful API for converting Minecraft Java Edition mods to Bedrock Edition add-ons. This document covers all av

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ModPorter AI - Comprehensive API Documentation

## 🚀 Overview

ModPorter AI provides a RESTful API for converting Minecraft Java Edition mods to Bedrock Edition add-ons. This document covers all available endpoints, authentication, best practices, and integration examples.

## 🌐 Base URLs

### Environments
- **Development**: `http://localhost:8000/api/v1`
- **Staging**: `https://staging-api.modporter.ai/v1`
- **Production**: `https://api.modporter.ai/v1`

### WebSocket Endpoints
- **Conversion Progress**: `ws://localhost:8000/ws/conversions/{conversion_id}`
- **Real-time Updates**: `wss://api.modporter.ai/ws/conversions/{conversion_id}`

## 🔐 Authentication & Security

### Current Status
- API is currently open for public use
- Authentication will be implemented in v2.0
- Rate limiting applies to all requests

### Rate Limiting
| Endpoint | Limit | Window |
|----------|-------|--------|
| Conversions | 10 per hour | per IP |
| File Uploads | 100MB per request | per request |
| General API | 1000 requests per hour | per IP |
| WebSocket Connections | 50 concurrent | per IP |

### Headers
```http
Content-Type: application/json
X-API-Version: 1.0 (optional)
User-Agent: YourApp/1.0 (recommended)
```

## 📊 Response Format

### Success Response
```json
{
  "success": true,
  "data": {
    // Response data
  },
  "message": "Operation completed successfully",
  "timestamp": "2025-01-01T12:00:00Z",
  "request_id": "req_550e8400-e29b-41d4-a716"
}
```

### Error Response
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input parameters",
    "details": {
      "field": "mod_file",
      "issue": "File size exceeds 100MB limit"
    }
  },
  "timestamp": "2025-01-01T12:00:00Z",
  "request_id": "req_550e8400-e29b-41d4-a716"
}
```

### HTTP Status Codes
| Code | Description |
|------|-------------|
| 200 | Success |
| 201 | Created |
| 202 | Accepted (async processing) |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | F

*[truncated — see source for full prompt]*