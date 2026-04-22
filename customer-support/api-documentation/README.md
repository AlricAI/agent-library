# Api Documentation

> Complete REST API reference for ModPorter AI conversion services.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ModPorter AI API Documentation

Complete REST API reference for ModPorter AI conversion services.

## Base URL

```
Production: https://api.modporter.ai/v1
Staging: https://api-staging.modporter.ai/v1
Development: http://localhost:8080/api/v1
```

## Authentication

Most endpoints require API key authentication:

```bash
curl -H "Authorization: Bearer YOUR_API_KEY" \
  https://api.modporter.ai/v1/conversions
```

**Get your API key**: [modporter.ai/dashboard/settings](https://modporter.ai/dashboard/settings)

## API Status

Check current API status and uptime:

```bash
curl https://status.modporter.ai
```

---

## Endpoints

### Conversions

#### Start Conversion

Convert a Java mod to Bedrock add-on.

**Endpoint**: `POST /conversions`

**Authentication**: Required (API Key)

**Request**:

```bash
curl -X POST https://api.modporter.ai/v1/conversions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -F "file=@mod.jar" \
  -F "options={\"complexity\":\"high\",\"optimize_assets\":true}"
```

**Parameters**:

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| file | File | Yes | Java mod file (.jar or .zip, max 100MB) |
| options | JSON | No | Conversion options (see below) |

**Conversion Options**:

```json
{
  "complexity": "low|medium|high",  // Default: auto-detect
  "optimize_assets": true,          // Optimize textures/sounds
  "include_source": false,          // Include Java source in report
  "experimental_features": false,    // Enable experimental conversions
  "target_bedrock_version": "1.20.40" // Target Bedrock version
}
```

**Response**:

```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "status": "processing",
  "created_at": "2026-03-27T15:30:00Z",
  "estimated_completion": "2026-03-27T15:35:00Z",
  "mod_info": {
    "name": "Ruby Sword Mod",
    "version": "1.0.0",
    "loader": "forge",
    "complexity": "simple"
  }
}
```

**Status Codes**:
- `201 Created`: Conversion started successfully
- `400 

*[truncated — see source for full prompt]*