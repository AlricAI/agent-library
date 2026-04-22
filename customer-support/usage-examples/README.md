# USAGE EXAMPLES

> This document provides comprehensive examples for using all four protocols supported by this Worker:
- **REST API** - Standard HTTP endpoints
- **WebS

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Multi-Protocol GitHub Worker - Usage Examples

This document provides comprehensive examples for using all four protocols supported by this Worker:
- **REST API** - Standard HTTP endpoints
- **WebSocket** - Real-time bidirectional communication
- **RPC** - Direct service binding invocations
- **MCP** - Model Context Protocol for AI tools

## Prerequisites

```bash
# Set your base URL and API key
export BASE_URL="https://your-worker.workers.dev"
export API_KEY="your-api-key-here"
```

---

## 1. REST API Examples

### Search Repositories

```bash
curl -X POST "$BASE_URL/api/octokit/search/repos" \
  -H "x-api-key: $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "q": "language:typescript stars:>100",
    "sort": "stars",
    "order": "desc",
    "per_page": 10
  }' | jq
```

### Create or Update a File

```bash
curl -X POST "$BASE_URL/api/tools/files/upsert" \
  -H "x-api-key: $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "owner": "your-username",
    "repo": "your-repo",
    "path": "src/index.ts",
    "content": "console.log(\"Hello from Worker!\");",
    "message": "Add index.ts",
    "branch": "main"
  }' | jq
```

### Create an Issue

```bash
curl -X POST "$BASE_URL/api/tools/issues/create" \
  -H "x-api-key: $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "owner": "your-username",
    "repo": "your-repo",
    "title": "Bug: Application crashes on startup",
    "body": "When I start the application, it crashes immediately.",
    "labels": ["bug", "urgent"]
  }' | jq
```

### Create a Pull Request

```bash
curl -X POST "$BASE_URL/api/tools/prs/create" \
  -H "x-api-key: $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "owner": "your-username",
    "repo": "your-repo",
    "title": "feat: Add new feature",
    "body": "This PR implements the requested feature.",
    "head": "feature-branch",
    "base": "main"
  }' | jq
```

### Create Agent Session

```bash
curl -X POST "$BASE_URL/api/agents/sessio

*[truncated — see source for full prompt]*