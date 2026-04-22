# COMPATIBILITY

> This document defines the API versioning strategy, compatibility matrix, deprecation policy, and version support lifecycle for VirtEngine.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VirtEngine API Compatibility

This document defines the API versioning strategy, compatibility matrix, deprecation policy, and version support lifecycle for VirtEngine.

## Table of Contents

- [Version Support Lifecycle](#version-support-lifecycle)
- [API Compatibility Matrix](#api-compatibility-matrix)
- [Protocol Version Negotiation](#protocol-version-negotiation)
- [Deprecation Policy](#deprecation-policy)
- [Breaking Change Guidelines](#breaking-change-guidelines)
- [Client Compatibility](#client-compatibility)

## Version Support Lifecycle

VirtEngine follows a **N-2 support policy**, meaning we support the current major/minor version plus two previous minor versions.

### Support Levels

| Level | Description | Duration |
|-------|-------------|----------|
| **Active** | Full support, new features, bug fixes | Current release |
| **Maintenance** | Security fixes and critical bugs only | N-1 and N-2 releases |
| **Deprecated** | No support, migration strongly encouraged | Beyond N-2 |
| **End of Life** | Not supported, may be removed | 6 months after deprecation |

### Current Version Support Matrix

| Version | Status | Release Date | EOL Date | Notes |
|---------|--------|--------------|----------|-------|
| v0.11.x | Active | TBD | TBD | Current development |
| v0.10.x | Maintenance | TBD | TBD | Latest mainnet |
| v0.9.x | Maintenance | TBD | TBD | Previous testnet |
| v0.8.x | Deprecated | TBD | TBD | Previous mainnet |
| < v0.8 | EOL | - | - | Not supported |

### Version Numbering Convention

- **Odd minor versions** (0.9.x, 0.11.x): Testnet releases
- **Even minor versions** (0.8.x, 0.10.x): Mainnet releases
- **Patch versions**: Bug fixes and security patches (backwards compatible)

## API Compatibility Matrix

### Module API Versions

| Module | Current Version | Supported Versions | Next Version |
|--------|-----------------|-------------------|--------------|
| `x/veid` | v1 | v1 | v2 (planned) |
| `x/mfa` | v1 | v1 | - |
| `x/encryption` | v1 | 

*[truncated — see source for full prompt]*