# WORKER API

> The Atlas Worker API enables distributed processing of transcription and content processing jobs across multiple machines (primarily Mac Mini workers).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas Worker API Documentation

The Atlas Worker API enables distributed processing of transcription and content processing jobs across multiple machines (primarily Mac Mini workers).

## Base URL
```
https://atlas.khamel.com/api/v1/worker
```

## API Endpoints

### 1. Worker Registration
**POST** `/register`

Register a new worker with Atlas to receive jobs.

**Request Body:**
```json
{
    "worker_id": "mac_mini_01",
    "capabilities": ["transcribe_youtube", "transcribe_podcast", "transcribe_url"],
    "platform": "mac",
    "whisper_available": true,
    "ytdlp_available": true,
    "metadata": {
        "location": "office",
        "specs": "M2 Mac Mini"
    }
}
```

**Response:**
```json
{
    "success": true,
    "message": "Worker mac_mini_01 registered"
}
```

### 2. Get Jobs
**GET** `/jobs?worker_id={id}&capabilities={caps}`

Retrieve available jobs for a specific worker.

**Parameters:**
- `worker_id` (required): Unique worker identifier
- `capabilities` (optional): Comma-separated list of job types this worker can handle

**Response:**
```json
{
    "jobs": [
        {
            "id": "e54d2bbe-abec-448a-870c-5c3ee19dbce9",
            "type": "transcribe_youtube",
            "data": {
                "url": "https://youtube.com/watch?v=example",
                "title": "Example Video"
            },
            "priority": 5,
            "created_at": "2025-08-25T23:42:59.854326"
        }
    ]
}
```

**Empty Response (No Jobs):**
```json
{
    "jobs": []
}
```

### 3. Submit Job Results
**POST** `/results`

Submit completed job results back to Atlas.

**Request Body:**
```json
{
    "job_id": "e54d2bbe-abec-448a-870c-5c3ee19dbce9",
    "worker_id": "mac_mini_01",
    "status": "completed",
    "result": {
        "transcript": "Full transcript text here...",
        "filename": "example_video.txt",
        "source_url": "https://youtube.com/watch?v=example",
        "title": "Example Video",
        "length": 300
    },
    "timestamp": 1693000

*[truncated — see source for full prompt]*