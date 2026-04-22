# API

> ## Base URL
- Development: `http://localhost:8000/api/v1`
- Production: `https://api.modporter.ai/v1`

## Authentication
Currently, the API is open fo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ModPorter AI API Documentation

## Base URL
- Development: `http://localhost:8000/api/v1`
- Production: `https://api.modporter.ai/v1`

## Authentication
Currently, the API is open for public use. Authentication will be added in future versions for rate limiting and user management.

## Endpoints

### Health Check
```http
GET /api/v1/health
```

**Response**
```json
{
  "status": "healthy",
  "version": "1.0.0",
  "timestamp": "2025-07-02T12:00:00Z"
}
```

### Start Conversion
```http
POST /convert
```

Implements PRD Feature 1: One-Click Modpack Ingestion

**Request Body (multipart/form-data)**
```
mod_file: File (optional) - .jar or .zip file
mod_url: string (optional) - CurseForge or Modrinth URL
smart_assumptions: boolean (default: true)
include_dependencies: boolean (default: true)
```

**Timeout**: Conversions have a maximum timeout of 10 minutes. If a conversion takes longer than this, it will be marked as failed.

**Response**
```json
{
  "conversion_id": "550e8400-e29b-41d4-a716-446655440000",
  "status": "processing",
  "overall_success_rate": 0.0,
  "converted_mods": [],
  "failed_mods": [],
  "smart_assumptions_applied": [],
  "download_url": null,
  "detailed_report": {
    "stage": "initialization",
    "progress": 0,
    "logs": [],
    "technical_details": {}
  }
}
```

### Get Conversion Status
```http
GET /convert/{conversion_id}/status
```

**Response**
```json
{
  "conversion_id": "550e8400-e29b-41d4-a716-446655440000",
  "status": "completed",
  "overall_success_rate": 85.5,
  "converted_mods": [
    {
      "name": "Iron Chests",
      "version": "1.19.2-14.4.4",
      "status": "success", 
      "features": [
        {
          "name": "Iron Chest Block",
          "type": "block",
          "converted": true,
          "changes": "Converted to custom block with container functionality"
        }
      ],
      "warnings": []
    }
  ],
  "failed_mods": [],
  "smart_assumptions_applied": [
    {
      "original_feature": "Custom GUI",
      

*[truncated — see source for full prompt]*