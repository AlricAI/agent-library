# 18 Testing Source Lib Tests

> ## Context

You are working on unit tests for the core library modules (`src/lib/`) and data source adapters (`src/sources/`) in crypto-vision.

**Exi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 18 — Testing: Source Adapter & Lib Module Tests

## Context

You are working on unit tests for the core library modules (`src/lib/`) and data source adapters (`src/sources/`) in crypto-vision.

**Existing lib tests** (in `src/lib/__tests__/` and `tests/lib/`):
agents, ai, api-error, anomaly, auth, bigquery, bq-ingest, cache, cdn-cache, embeddings, env, etag, export-manager, fallback, fetcher, logger, metrics, middleware, orchestrator, pubsub, queue, rag, rate-limit, redis, response-envelope, schemas, search-analytics, search, security, training-config, validation, vector-store, workflow-templates, ws

**Existing source tests** (in `src/sources/__tests__/`): Unknown — audit what exists.

## Task

### 1. Audit Existing Lib Tests

Run all existing lib tests and fix failures:
```bash
npm test -- --reporter=verbose 2>&1 | head -200
```

For each failing test, fix the test or the underlying code.

### 2. Write Source Adapter Tests

Each source adapter needs tests. These should mock HTTP responses (not call real APIs):

**Pattern:**
```typescript
import { describe, it, expect, vi, beforeEach } from 'vitest';
import { someAdapter } from '../some-source.js';

// Mock the fetcher
vi.mock('../../lib/fetcher.js', () => ({
  fetchWithResilience: vi.fn(),
}));

describe('SomeSource', () => {
  it('returns parsed data on success', async () => {
    vi.mocked(fetchWithResilience).mockResolvedValue({
      ok: true,
      json: async () => mockApiResponse,
    });
    const result = await someAdapter.getData();
    expect(result).toEqual(expectedParsedData);
  });

  it('handles API errors', async () => {
    vi.mocked(fetchWithResilience).mockResolvedValue({
      ok: false,
      status: 429,
    });
    await expect(someAdapter.getData()).rejects.toThrow();
  });

  it('handles network failures', async () => {
    vi.mocked(fetchWithResilience).mockRejectedValue(new Error('fetch failed'));
    await expect(someAdapter.getData()).rejects.toThrow();
  });
});
```

**Source

*[truncated — see source for full prompt]*