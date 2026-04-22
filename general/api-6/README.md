# Api

> ## Quick Start

Here's a common workflow for working with the Remarq API:

```bash
# 1. Create a comment on a document (auto-creates document if neede

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Remarq API Documentation

## Quick Start

Here's a common workflow for working with the Remarq API:

```bash
# 1. Create a comment on a document (auto-creates document if needed)
curl -X POST http://localhost:3000/comments \
  -H "Content-Type: application/json" \
  -d '{
    "uri": "https://example.com/article",
    "quote": "selected text from the page",
    "body": "This is my first comment",
    "author": "Alice"
  }'

# Response: { "id": "cmt_xyz", "status": "open", ... }

# 2. Create a reply to the comment
curl -X POST http://localhost:3000/comments \
  -H "Content-Type: application/json" \
  -d '{
    "document": "doc_abc",
    "parent": "cmt_xyz",
    "body": "Great point!",
    "author": "Bob"
  }'

# 3. Resolve the original comment
curl -X PATCH http://localhost:3000/comments/cmt_xyz \
  -H "Content-Type: application/json" \
  -d '{ "status": "closed" }'

# 4. List all open comments for the document
curl "http://localhost:3000/comments?uri=https://example.com/article&status=open"
```

---

## Base URL

When running locally:

```
http://localhost:3000
```

When deployed, replace with your server's URL.

---

## Endpoints

### Health Check

#### `GET /health`

Check if the server is running.

**Response:**

```json
{
  "status": "ok"
}
```

**Status Codes:**

- `200 OK` — Server is healthy

**Example:**

```bash
curl http://localhost:3000/health
```

---

### Documents

#### `GET /documents`

List all documents.

**Response:**

```json
{
  "object": "list",
  "data": [
    {
      "id": "doc_k3mXp9q2aBvN",
      "object": "document",
      "uri": "https://example.com/article",
      "created_at": "2026-02-21T10:30:00.000Z"
    }
  ]
}
```

**Status Codes:**

- `200 OK` — Returns list of documents

**Example:**

```bash
curl http://localhost:3000/documents
```

---

#### `POST /documents`

Create a new document (or return existing if URI already exists).

**Request Body:**

```json
{
  "uri": "https://example.com/article"
}
```

**Response (201 Created):**


*[truncated — see source for full prompt]*