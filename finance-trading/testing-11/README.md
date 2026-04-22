# TESTING

> > Comprehensive testing guide for the `crypto-vision` monorepo.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Testing Strategy

> Comprehensive testing guide for the `crypto-vision` monorepo.

## Table of Contents

1. [Overview](#overview)
2. [Test Categories](#test-categories)
3. [Running Tests](#running-tests)
4. [Test Structure](#test-structure)
5. [Writing Tests](#writing-tests)
6. [Coverage](#coverage)
7. [CI Integration](#ci-integration)
8. [Package Testing](#package-testing)

---

## Overview

Crypto Vision uses [Vitest](https://vitest.dev) as the test runner with a multi-layer testing strategy:

| Layer | Purpose | Speed | Count |
|-------|---------|-------|-------|
| Unit | Individual functions and modules | Fast (<1s) | ~33 files |
| Route | HTTP route handler behavior | Fast (<2s) | ~10 files |
| Integration | Multi-route API flows | Medium (~5s) | 1 file |
| E2E | Full server smoke tests | Slow (~30s) | 1 file |
| Fuzz | Random input robustness | Medium | 1 file |
| Benchmark | Performance regression | Variable | 1 file |
| Load | Stress/soak/smoke profiles | Long | 3 files |

---

## Test Categories

### Unit Tests (`tests/lib/`)

Test individual library modules in isolation:

```
tests/lib/
├── cache.test.ts              # Cache operations (get, set, TTL, eviction)
├── auth.test.ts               # API key validation
├── fetcher.test.ts            # HTTP fetch with circuit breaker
├── anomaly.test.ts            # Anomaly detection algorithms
├── anomaly-processors.test.ts # Anomaly signal processors
├── embeddings.test.ts         # Embedding generation and storage
├── queue.test.ts              # Request queue management
├── rate-limit.test.ts         # Rate limiter behavior
├── search.test.ts             # Semantic search logic
├── security.test.ts           # Security header validation
├── validation.test.ts         # Zod schema validation
├── ...                        # (33 total test files)
```

### Route Tests (`tests/routes/`)

Test HTTP endpoints including request validation, response format, and error handling:

```
tests/routes/
├── market.test.ts  

*[truncated — see source for full prompt]*