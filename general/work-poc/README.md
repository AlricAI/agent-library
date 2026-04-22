# Work Poc

> This document outlines the first two implementation phases for the `work` CLI, focusing on establishing a solid foundation and delivering a functional MVP with the local-fs adapter.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# work CLI — Proof of Concept Implementation Plan

This document outlines the first two implementation phases for the `work` CLI, focusing on establishing a solid foundation and delivering a functional MVP with the local-fs adapter.

---

## Phase 1: Project Scaffolding

### 1.1 Objectives

Establish a professional, first-class CLI project foundation that supports:

- Modern TypeScript development workflow
- Testing pyramid implementation
- CI/CD pipeline
- Documentation generation
- Release management

### 1.2 Deliverables

#### Project Structure

```
work-cli/
├── src/
│   ├── cli/           # Command parsing and CLI interface
│   ├── core/          # Core engine and graph logic
│   ├── adapters/      # Adapter implementations
│   ├── types/         # TypeScript type definitions
│   └── utils/         # Shared utilities
├── tests/
│   ├── unit/          # Unit tests (70%)
│   ├── integration/   # Integration tests (20%)
│   └── e2e/           # End-to-end tests (10%)
├── docs/              # Documentation (current content)
├── examples/          # Usage examples and demos
├── scripts/           # Build and development scripts
├── Makefile           # Unified development commands
└── .pre-commit-config.yaml  # Pre-commit hook configuration
```

#### Development Infrastructure

- **Package Management**: npm/yarn with lockfile
- **TypeScript Configuration**: Strict mode, path mapping
- **Testing Framework**: Jest with coverage reporting
- **Linting**: ESLint + Prettier
- **Build System**: TypeScript compiler + bundling
- **CI/CD**: GitHub Actions for test/build/release
- **Makefile**: Unified command interface for all development tasks
- **Pre-commit Hooks**: Automated code quality checks before commits

#### Documentation System

- **API Documentation**: TypeDoc generation
- **CLI Help**: Built-in help system
- **Examples**: Working code samples
- **Contributing Guide**: Development workflow

### 1.3 Success Criteria

- [ ] Clean `npm install && npm test && npm buil

*[truncated — see source for full prompt]*