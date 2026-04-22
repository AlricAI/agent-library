# QUICKSTART

> This guide helps you quickly test the new WebSocket and Conversion API implementation.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Quick Start Guide: WebSocket & Conversion API

This guide helps you quickly test the new WebSocket and Conversion API implementation.

## Prerequisites

- Python 3.9+
- Docker and Docker Compose (recommended)
- OR local PostgreSQL and Redis

## 1. Start the Backend

### Using Docker (Recommended)

```bash
cd /home/alexc/Projects/ModPorter-AI

# Start with hot reload
docker compose -f docker compose.dev.yml up -d backend

# View logs
docker compose logs -f backend

# Backend will be available at: http://localhost:8080
```

### Using Local Environment

```bash
cd backend

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your DATABASE_URL and REDIS_URL

# Start the server
python src/main.py
```

## 2. Verify the Server is Running

```bash
# Health check
curl http://localhost:8080/api/v1/health

# Expected response:
# {
#   "status": "healthy",
#   "version": "1.0.0",
#   "timestamp": "2025-02-12T10:30:00.123456"
# }
```

## 3. Test REST API Endpoints

### Create a Conversion

```bash
# Prepare a test JAR file (or use an existing mod)
# For testing, we can create a simple file
echo "fake jar content" > test_mod.jar

# Create conversion
curl -X POST http://localhost:8080/api/v1/conversions \
  -F "file=@test_mod.jar" \
  -F 'options={"assumptions":"conservative","target_version":"1.20.0"}'

# Save the conversion_id from the response, e.g.:
# {"conversion_id":"550e8400-e29b-41d4-a716-446655440000",...}

CONVERSION_ID="550e8400-e29b-41d4-a716-446655440000"
```

### Get Conversion Status

```bash
curl http://localhost:8080/api/v1/conversions/$CONVERSION_ID

# Example response:
# {
#   "conversion_id": "550e8400-e29b-41d4-a716-446655440000",
#   "status": "processing",
#   "progress": 45,
#   "message": "JavaAnalyzerAgent is analyzing mod structure...",
#   "created_at": "2025-02-12T10:30:00Z",
#   "updated_at": "2025-02-12T10:35:00Z",
#   "result_url": null,
#   "error": null,
#   "original_filena

*[truncated — see source for full prompt]*