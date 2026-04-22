# Monorepo Documentation Strategy

> description: Documentation strategy and hierarchy for the monorepo globs: - "docs/**/*"

## Tags
`react`

## System Prompt
---
description: Documentation strategy and hierarchy for the monorepo
globs:
  - "docs/**/*"
  - "**/README.md"
  - "**/CHANGELOG.md"
scopes:
  - documentation
  - monorepo
alwaysApply: false
---
# Monorepo Documentation Strategy

<!-- ==================== METADATA ==================== -->
ruleType: always
description: >
  Comprehensive documentation strategy for monorepo projects covering location, format,
  maintenance, and cross-referencing standards.
whenToUse:
  - Creating new documentation
  - Updating existing documentation
  - After completing any feature or refactor
  - When adding new packages or apps to the monorepo
# =====================================================

## 📂 Documentation Location Hierarchy

The monorepo uses a hierarchical documentation approach to ensure domain knowledge is stored at the appropriate scope level.

### 1. Package/App-Level Documentation
- **Primary Location:** Inside each package or app in a `docs/` subfolder
  ```
  packages/ui/docs/            # UI package-specific docs
  apps/web/docs/               # Web app-specific docs
  ```
- **Purpose:** Package-specific implementation details, API usage, internal patterns

### 2. Feature-Level Documentation
- **Location:** `/docs/features/[feature-name]/`
- **Purpose:** Documentation for features that span multiple packages

### 3. Global Documentation
- **Location:**
  ```
  /docs/architecture/          # System-wide architecture
  /docs/concepts/              # Shared concepts and patterns
  /docs/architecture/adr/      # Architecture Decision Records
  ```
- **Purpose:** Project-wide knowledge and design decisions

### Documentation Placement Decision Matrix

| Documentation Type | Placement Location |
|--------------------|-------------------|
| Feature spanning multiple packages | `/docs/features/[feature-name]/` |
| Implementation in shared workspace package | `packages/[pkg]/docs/` |
| Package-level setup or design notes | `packages/[pkg]/README.md` or `packages/[pkg]

*[truncated — see source for full prompt]*