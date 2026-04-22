# Project Docs

> Thank you for your interest in contributing to ModPorter AI!

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Contributing Guidelines

Thank you for your interest in contributing to ModPorter AI! This document provides guidelines for contributing to the project.

## Development Setup

### Prerequisites
- Node.js 18+ and pnpm 7+
- Python 3.9+ and pip
- Docker and Docker Compose (optional but recommended)
- Git

### Quick Start
```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/ModPorter-AI.git
cd ModPorter-AI

# Install all dependencies
pnpm run install-all

# Start development environment
docker compose up -d

# Or start services individually
pnpm run dev
```

## Project Structure

```
ModPorter-AI/
├── frontend/          # React TypeScript frontend
├── backend/           # Python FastAPI backend  
├── ai-engine/         # CrewAI conversion engine
├── local-agent/       # Node.js local validation agent
├── docs/              # Documentation
└── tests/             # Integration tests
```

## Development Workflow

### 1. Test-Driven Development (TDD)
We follow TDD principles as specified in the PRD:

```bash
# Write tests first
pnpm run test:watch

# Implement feature
# Run tests to verify
pnpm run test
```

### 2. Code Quality Standards
- **Frontend**: ESLint + Prettier for TypeScript/React
- **Backend**: Flake8 + Black for Python
- **Testing**: Jest (frontend), pytest (backend)
- **Coverage**: Minimum 80% test coverage required

### 3. Commit Convention
We use Conventional Commits:
```
feat: add smart assumption for custom dimensions
fix: resolve file upload validation issue
docs: update API documentation
test: add conversion crew unit tests
```

### 4. Pull Request Process
1. Fork the repository
2. Create feature branch: `git checkout -b feature/amazing-feature`
3. Write tests following TDD approach
4. Implement feature according to PRD specifications
5. Ensure all tests pass: `pnpm run test`
6. Submit pull request with clear description

## PRD Compliance

All contributions must align with the Product Requirements Document:

### Core Features (Mus

*[truncated — see source for full prompt]*