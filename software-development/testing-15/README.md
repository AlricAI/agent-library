# Testing

> Genonaut uses a comprehensive three-tier testing approach to ensure code quality and reliability across all components.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Testing Documentation

Genonaut uses a comprehensive three-tier testing approach to ensure code quality and reliability across all components.

## Related documentation
- `test-troubleshooting-db-and-server.md`: When to read this? If you are having difficulties with tests involving: database setup, server startup, and E2E test execution.

## Test Worktree Setup

**IMPORTANT**: If you are working in a secondary git worktree (e.g., `/Users/joeflack4/projects/genonaut-wt2`), you must use dedicated infrastructure to avoid port conflicts with the main worktree.

See [testing-test-worktree.md](./testing-test-worktree.md) for complete instructions on:
- Starting worktree-specific services (API, Celery, Frontend)
- Running tests against the correct infrastructure
- Port and queue separation strategy
- Troubleshooting worktree-specific issues

**Quick Reference for Worktree 2:**
- Starting services: `make api-test-wt2` and `make celery-test-wt2` (and also `make frontend-dev-wt2` if needed)
- Running tests: `make test-wt2`, `make test-api-wt2`, `make frontend-test-e2e-wt2`

## API Server Management for Testing

**IMPORTANT**: When working with test API servers, use the environment-specific stop and restart commands instead of manually killing processes with `pkill` or `killall`.

**Why this matters:**
- Prevents accidentally killing API servers in other worktrees
- Pattern-matches on exact `--env-target` flag for precise targeting
- Includes proper cleanup with a 3-second wait period
- Essential when debugging test failures that may be caused by stale server state

**Common Testing Scenarios:**

**Restarting After Code Changes:**
```bash
# After changing Pydantic models or other non-hot-reload code:
make api-test-wt2-restart

# Or manually:
make api-test-wt2-stop
# ... clear Python bytecode cache if needed ...
make api-test-wt2
```

**Clearing Python Bytecode Cache:**
```bash
# When Uvicorn auto-reload doesn't pick up changes:
find . -type d -name __pycache__ -exec rm -rf {

*[truncated — see source for full prompt]*