# E2e Testing

> ## Overview

CodeFRAME has comprehensive E2E test coverage with 47 tests (10 backend Pytest, 37 frontend Playwright) validating the complete autonomou

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# End-to-End Testing (E2E)

## Overview

CodeFRAME has comprehensive E2E test coverage with 47 tests (10 backend Pytest, 37 frontend Playwright) validating the complete autonomous workflow from discovery through completion.

## Running E2E Tests

### Frontend Tests (Playwright)

```bash
cd tests/e2e
npx playwright test  # Backend auto-starts on port 8080
```

**What happens automatically**:
1. Backend server starts with health check on port 8080
2. Frontend dev server starts on port 3000
3. Database seeding runs (via global-setup.ts)
4. Tests execute across browsers (Chromium, Firefox, WebKit)
5. Servers shut down after completion

### Backend Tests (Pytest)

```bash
uv run pytest tests/e2e/test_*.py -v -m "e2e"
```

## Key Configuration

### Playwright Auto-Start

`tests/e2e/playwright.config.ts`:
```typescript
webServer: [
  {
    command: 'cd ../.. && uv run uvicorn codeframe.ui.server:app --port 8080',
    url: 'http://localhost:8080/health',
    timeout: 120000,
    reuseExistingServer: !process.env.CI
  },
  // Frontend server config...
]
```

### Health Endpoint

`codeframe/ui/server.py`:
```python
@app.get("/health")
async def health_check():
    return {"status": "ok"}
```

## Troubleshooting

### Port 8080 already in use

```bash
# Check what's using port 8080
lsof -i:8080

# If it's a CodeFrame server you want to stop:
lsof -ti:8080 -c python | xargs kill

# Only use kill -9 as last resort (kills ALL processes on port)
# lsof -ti:8080 | xargs kill -9  # ⚠️  Use with caution

# Alternative: Let Playwright reuse the existing server
# (enabled by default via reuseExistingServer: true in playwright.config.ts)
```

### Backend health check timeout

```bash
# Test backend manually (from project root)
uv run uvicorn codeframe.ui.server:app --port 8080
curl http://localhost:8080/health  # Should return {"status": "ok"}
```

### Database seeding errors

```bash
# Remove test databases if needed (rarely necessary)
rm -f tests/e2e/fixtures/*/test_state.db
rm -f .cod

*[truncated — see source for full prompt]*