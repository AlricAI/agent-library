# Flagging Quickstart

> Get the content flagging system up and running in 5 minutes!

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Content Flagging System - Quick Start Guide

Get the content flagging system up and running in 5 minutes!

## Prerequisites

- Python 3.10+
- Node.js 18+
- PostgreSQL
- Project already set up with `make init`

## 1. Configure Flag Words (2 minutes)

Create your flag words list:

```bash
# Copy example file
cp docs/flag-words.txt.example flag-words.txt

# Edit to add your words
nano flag-words.txt
```

**Example flag-words.txt:**
```
# Violence & Weapons
violence
weapon
gun
combat

# Hate Speech
hatred
racist
slur

# Explicit Content
explicit
nude
sexual
```

**Important:** The `flag-words.txt` file is in `.gitignore` - never commit it!

## 2. Start Backend (1 minute)

```bash
# Start API server (development database)
make api-dev

# Or use test database
make api-test
```

**Verify it's running:**
```bash
curl http://localhost:8001/api/v1/health
# Should return: {"status":"healthy"}
```

## 3. Start Frontend (1 minute)

```bash
cd frontend
npm install  # First time only
npm run dev
```

**Access the UI:**
- Frontend: http://localhost:5173
- Admin Page: http://localhost:5173/admin/flagged-content

## 4. Test It Out (1 minute)

### Create Flagged Content via API

```bash
curl -X POST http://localhost:8001/api/v1/content \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Test Content",
    "content_type": "regular",
    "item_metadata": {
      "prompt": "A scene with violence and weapons"
    },
    "creator_id": "121e194b-4caa-4b81-ad4f-86ca3919d5b9"
  }'
```

### View Flagged Content

**Via API:**
```bash
curl http://localhost:8001/api/v1/admin/flagged-content/ | jq
```

**Via UI:**
1. Navigate to http://localhost:5173/admin/flagged-content
2. See your flagged content in the table!
3. Click the eye icon to view details
4. Try filtering, reviewing, or deleting

## 5. Key Features to Try

### Risk Scoring

Content is automatically scored 0-100:
- **0-25**: Low Risk (Green)
- **26-50**: Medium Risk (Yellow)
- **51-75**: High Risk (Orange)
- **76-100**: Cr

*[truncated — see source for full prompt]*