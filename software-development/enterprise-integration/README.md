# ENTERPRISE INTEGRATION

> This guide covers enterprise-level integration patterns, best practices, and operational considerations for using qtests in production environments.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Enterprise Integration Guide

This guide covers enterprise-level integration patterns, best practices, and operational considerations for using qtests in production environments.

## 🏢 Enterprise Setup

### Repository Structure

```
monorepo/
├── packages/
│   ├── frontend/          # React/Next.js application
│   ├── backend-api/        # Node.js API service
│   ├── shared-types/      # TypeScript type definitions
│   └── test-utils/        # Shared testing utilities
├── tests/
│   ├── integration/        # Cross-package integration tests
│   ├── e2e/             # End-to-end tests
│   ├── performance/        # Performance benchmarks
│   └── fixtures/          # Test data and mock servers
├── pipelines/             # CI/CD configurations
└── infrastructure/       # Docker, Terraform, etc.
```

### Package.json Configuration

```json
{
  "name": "enterprise-app",
  "private": true,
  "workspaces": [
    "packages/*"
  ],
  "scripts": {
    "test:unit": "jest --testPathPattern=packages/*/src/**/*.test.ts",
    "test:integration": "jest --config=tests/integration/jest.config.mjs",
    "test:e2e": "jest --config=tests/e2e/jest.config.mjs",
    "test:performance": "node tests/performance/run-benchmarks.js",
    "test:all": "npm run test:unit && npm run test:integration && npm run test:e2e",
    "test:coverage": "jest --coverage --collectCoverageFrom=\"packages/*/src/**/*.{ts,tsx}\"",
    "test:ci": "CI=true npm run test:all",
    "test:watch": "jest --watch --testPathPattern=packages/*/src"
  },
  "devDependencies": {
    "qtests": "^4.0.0",
    "jest": "^29.7.0",
    "ts-jest": "^29.4.1",
    "@types/jest": "^30.0.0"
  }
}
```

## 🔄 CI/CD Integration

### GitHub Actions Enterprise Workflow

```yaml
# .github/workflows/enterprise-tests.yml
name: Enterprise Test Suite

on:
  push:
    branches: [main, develop, release/*]
  pull_request:
    branches: [main, develop]

env:
  NODE_VERSION: '20'
  CACHE_VERSION: v1

jobs:
  setup:
    runs-on: ubuntu-latest
    outputs:

*[truncated — see source for full prompt]*