# TESTING

> Lumineer uses a **3-layer test strategy** that balances fast feedback (unit tests on every commit) with deep quality validation (RAG evaluation on LLM-related changes).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Testing Guide

Lumineer uses a **3-layer test strategy** that balances fast feedback (unit tests on every commit) with deep quality validation (RAG evaluation on LLM-related changes).

---

## Test Pyramid

```mermaid
pyramid
    title Lumineer Test Pyramid
    "E2E Agent Tests (LLM-as-Judge)" : 10
    "RAG Evaluation (DeepEval + Golden Dataset)" : 30
    "Unit Tests (Vitest / pytest)" : 60
```

| Layer | Tools | When to run | Gate |
|-------|-------|-------------|------|
| **Layer 1** Unit Tests | Vitest (TS) · pytest (Python) | Every commit | CI required |
| **Layer 2** RAG Evaluation | DeepEval + Golden Dataset | LLM-related PRs only | CI required (Tier 1) |
| **Layer 3** E2E Agent Tests | LLM-as-Judge | Pre-release / manual | Manual |

---

## Layer 1 — Unit Tests

### Running tests

```bash
# Frontend
cd frontend && bun test
cd frontend && bun test:watch              # watch mode
cd frontend && bun test src/features/auth  # single directory

# Backend
cd backend && bun test
cd backend && bun test:watch

# AI Processing
cd ai && pytest
cd ai && pytest -v                         # verbose
cd ai && pytest tests/test_formatters.py  # single file
cd ai && pytest -k "reranker"             # keyword filter
```

### TypeScript tests (Vitest)

Vitest is used for both Frontend and Backend. It is Jest-compatible but Vite-native.

```typescript
// Import from vitest — never from jest
import { describe, it, expect, vi } from "vitest"

// Mock modules
vi.mock("@/lib/hooks/useApi")

// Mock functions
const mockFn = vi.fn().mockResolvedValue({ data: [] })
```

**What to test:**
- Domain use cases (mocking Port interfaces — no real DB/network)
- Formatters (input/output deterministic)
- Reranker strategies (deterministic scoring)
- Zod validation schemas
- React components via React Testing Library

### Python tests (pytest)

```python
# pytest + pytest-asyncio for async routes
import pytest
from httpx import AsyncClient

@pytest.mark.asyncio
async def test_search_returns_res

*[truncated — see source for full prompt]*