# Monorepo README & Changelog Management

> description: Package documentation and versioning standards globs: - "packages/*/README.md"

## Tags
`typescript`

## System Prompt
---
description: Package documentation and versioning standards
globs:
  - "packages/*/README.md"
  - "packages/*/CHANGELOG.md"
  - "packages/*/package.json"
scopes:
  - documentation
  - versioning
  - packages
alwaysApply: false
---
# Monorepo README & Changelog Management

<!-- ==================== METADATA ==================== -->
whenToUse:
  - Creating a new package or app in the monorepo
  - Making changes to any existing package
  - Releasing a new version of any package
  - Adding features, fixing bugs, or making breaking changes
  - Updating workspace configuration or dependencies
description: >
  Comprehensive standards for monorepo documentation lifecycle: package READMEs, changelogs, 
  and versioning. Ensures consistent documentation and versioning across all workspace packages.
# =====================================================

## Related Rules:
# - Required foundation: monorepo-library-setup.rules.mdc (base monorepo structure)
# - Broader documentation: monorepo-documentation-strategy.rules.mdc (general docs)
# - Consider with: monorepo-contributing.rules.mdc (for open source projects)

## 1. Documentation File Validation (MANDATORY)

Every package in the monorepo MUST maintain these fundamental files:

| File | Purpose | Required Sections |
|------|---------|-------------------|
| `README.md` | Package description, installation, usage | Overview, Installation, Usage, API (if applicable) |
| `CHANGELOG.md` | Version history, release notes | Unreleased, Previous Versions |
| `package.json` | Package metadata, dependencies | name, version (must follow SemVer) |

### Automated Validation

When working with any package, the agent MUST:

1. Check for the existence of all required files
2. If any file is missing, automatically create it using the templates in section 6
3. Report the creation: "Created missing [filename] for [package]"
4. Never consider a task complete until all packages modified have valid documentation

## 2. README.md Requirements


*[truncated — see source for full prompt]*