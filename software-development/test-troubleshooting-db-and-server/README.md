# Test Troubleshooting Db And Server

> This guide covers common issues and solutions when working with Genonaut's test infrastructure, including database setup, server startup, and E2E test execution.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Test Database and Server Troubleshooting Guide

This guide covers common issues and solutions when working with Genonaut's test infrastructure, including database setup, server startup, and E2E test execution.

## Quick Diagnostic Commands

```bash
# Check if test database is accessible
python -c "from genonaut.db.init import get_database_url; print(get_database_url('test'))"

# Check if test server is running
curl -f http://localhost:8002/api/v1/health || echo "Test server not responding"

# Check test data seed status
python -m genonaut.db.init --check-playwright-fixtures

# Verify environment variables
python -c "import os; print('APP_ENV:', os.getenv('APP_ENV', 'Not set')); print('DATABASE_URL_TEST:', os.getenv('DATABASE_URL_TEST', 'Not set'))"
```

## Common Issues and Solutions

### Database Issues

#### Issue: "Database connection failed" or "relation does not exist"

**Symptoms:**
- Backend tests fail with connection errors
- API server won't start
- Migration errors

**Solutions:**

```bash
# 1. Check database connection
psql $DATABASE_URL_TEST -c "SELECT 1;" || echo "Connection failed"

# 2. Reinitialize test database
make init-test

# 3. For PostgreSQL test database
make init-test

# 4. Check environment variables
echo "DATABASE_URL_TEST: $DATABASE_URL_TEST"
echo "DATABASE_URL: $DATABASE_URL"
```

#### Issue: "Test data insufficient" or "Zero results" in Playwright tests

**Symptoms:**
- Playwright real API tests skip with "insufficient test data"
- Gallery tests show zero results
- Pagination tests can't run

**Solutions:**

```bash
# 1. Check current test data
python -m genonaut.db.init --check-playwright-fixtures

# 2. Re-export fresh test data from demo database
make export-demo-data

# 3. Reinitialize with new data
make init-test

# 4. Verify data was loaded
PGPASSWORD=$POSTGRES_PASSWORD psql -h localhost -U $POSTGRES_USER -d $POSTGRES_DB_TEST -c "
SELECT
  (SELECT COUNT(*) FROM content_items) as content_items,
  (SELECT COUNT(*) FROM content_items

*[truncated — see source for full prompt]*