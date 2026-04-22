# ASYNC TESTING GUIDE

> ## The Problem

FastAPI's `TestClient` runs synchronously but async database operations need an async context. This creates a compatibility issue wher

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# FastAPI + Async Database Testing Guide

## The Problem

FastAPI's `TestClient` runs synchronously but async database operations need an async context. This creates a compatibility issue where:

1. `TestClient` uses `requests` library internally (synchronous)
2. Async database operations require an event loop
3. The two don't work together seamlessly

## Common Error Patterns

```python
# This WILL FAIL with async database operations
from fastapi.testclient import TestClient

def test_endpoint():
    client = TestClient(app)
    response = client.post("/api/users", json={"name": "test"})
    # If the endpoint uses async database operations, this may hang or fail
```

## How Others Handle This Issue

### 1. **httpx.AsyncClient** (Recommended)
Most modern FastAPI projects use `httpx.AsyncClient` instead of `TestClient`:

```python
import httpx
import pytest
from httpx import ASGITransport

@pytest.mark.asyncio
async def test_endpoint():
    transport = ASGITransport(app=app)
    async with httpx.AsyncClient(transport=transport, base_url="http://testserver") as client:
        response = await client.post("/api/users", json={"name": "test"})
        assert response.status_code == 200
```

### 2. **pytest-asyncio** Configuration
Configure pytest to handle async tests properly:

```ini
# pytest.ini
[pytest]
asyncio_mode = auto
asyncio_default_fixture_loop_scope = session
asyncio_default_test_loop_scope = function
```

### 3. **Async Database Fixtures**
Create async database fixtures that work with the same event loop:

```python
@pytest.fixture
async def async_db_session():
    engine = create_async_engine("sqlite+aiosqlite:///:memory:")
    async with engine.begin() as conn:
        await conn.run_sync(Base.metadata.create_all)
    
    async_session = async_sessionmaker(engine, expire_on_commit=False)
    async with async_session() as session:
        yield session
    
    await engine.dispose()
```

## Our Solution

We've implemented a comprehensive solution in `bac

*[truncated — see source for full prompt]*