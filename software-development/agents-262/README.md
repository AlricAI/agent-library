# AGENTS

> This file provides guidance to Claude Code when working with frontend code in this repository.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Frontend Development Guide

This file provides guidance to Claude Code when working with frontend code in this repository.

## Project Overview
React + TypeScript + Vite frontend with Material UI, React Router, and React Query for data fetching.

## Environment Setup
**IMPORTANT**: Before starting frontend work:
```bash
cd frontend
npm install
```

## Code Style & Architecture
- Use TypeScript with strict typing for all function parameters
- Follow React best practices with hooks and functional components
- Use React Query for all data fetching and caching
- Prefer pure functions and avoid side effects where possible
- Instrument UI markup with stable `data-testid` attributes so components are easy to reference in reviews, automated tests, and debugging tools. See **Data Test IDs** below for conventions.

## Key Libraries & Patterns
- **Routing**: `react-router-dom@7`
- **Styling**: Material UI with custom `ThemeModeProvider`
- **Data Fetching**: `@tanstack/react-query` via service hooks
- **HTTP Client**: `ApiClient` + domain services (`UserService`, `GalleryService`, etc.)
- **Testing**: Vitest + Testing Library + MSW for mocking

## Testing Strategy
Follow comprehensive testing approach:
```bash
# Unit tests (fastest)
npm run test-unit
make frontend-test-unit

# All tests (unit + e2e)
npm run test
make frontend-test

# E2E tests only (Playwright)
npm run test:e2e
make frontend-test-e2e

# Development
npm run test:watch        # Auto-run tests on changes
npm run test:coverage     # Coverage reporting
```

## Development Workflow
```bash
# Development server
npm run dev               # http://localhost:5173
make frontend-dev

# Code quality
npm run lint              # ESLint checks
npm run type-check        # TypeScript validation
npm run build             # Production build
```

## Testing Requirements
- **Unit Tests**: >90% coverage for components, hooks, services
- **E2E Tests**: Cover critical user journeys
- Write tests during development, not after
- Mock e

*[truncated — see source for full prompt]*