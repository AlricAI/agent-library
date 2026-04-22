# Api

> ## Overview

The Atlas API provides programmatic access to all cognitive amplification features of the Atlas platform. It follows REST principles and 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas API Documentation

## Overview

The Atlas API provides programmatic access to all cognitive amplification features of the Atlas platform. It follows REST principles and uses JSON for request and response bodies.

## Base URL

```
https://atlas.khamel.com/api/v1
```

## Authentication

Most API endpoints require authentication via an API key. To generate an API key:

```bash
curl -X POST "https://atlas.khamel.com/api/v1/auth/generate" \
     -H "Content-Type: application/json" \
     -d '{"name": "my_api_key"}'
```

Include the API key in the `Authorization` header for authenticated requests:

```bash
curl -H "Authorization: Bearer YOUR_API_KEY" \
     https://atlas.khamel.com/api/v1/content/
```

## Content Management

### List Content

Get a list of all content with pagination and filtering options.

```http
GET /content/
```

**Query Parameters:**
- `skip` (int, optional): Number of items to skip (default: 0)
- `limit` (int, optional): Maximum number of items to return (default: 50)
- `content_type` (string, optional): Filter by content type (article, youtube, podcast)
- `tags` (array, optional): Filter by tags

**Response:**
```json
{
  "items": [
    {
      "uid": "abc123",
      "title": "Example Content",
      "source": "https://example.com",
      "content_type": "article",
      "status": "success",
      "created_at": "2023-01-01T00:00:00",
      "updated_at": "2023-01-01T00:00:00",
      "tags": ["example", "test"],
      "content_path": "/path/to/content.md"
    }
  ],
  "total": 1
}
```

### Get Content

Get details for a specific content item by ID.

```http
GET /content/{content_id}
```

### Submit URL for Processing

Submit a URL for content processing.

```http
POST /content/submit-url
```

**Request Body:**
```json
{
  "url": "https://example.com/article"
}
```

### Upload File for Processing

Upload a file for content processing.

```http
POST /content/upload-file
```

**Form Data:**
- `file`: The file to upload

### Delete Content

Delet

*[truncated — see source for full prompt]*