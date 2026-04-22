# CONFIGURATION

> This guide provides comprehensive information about configuring Atlas for different environments and use cases.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas Configuration Guide

This guide provides comprehensive information about configuring Atlas for different environments and use cases.

## Table of Contents

- [Configuration Overview](#configuration-overview)
- [Environment Setup](#environment-setup)
- [Configuration Files](#configuration-files)
- [Environment Variables](#environment-variables)
- [Secret Management](#secret-management)
- [Configuration Validation](#configuration-validation)
- [Advanced Configuration](#advanced-configuration)
- [Troubleshooting](#troubleshooting)

## Configuration Overview

Atlas uses a hierarchical configuration system that supports:

- **Environment-specific settings** (development, staging, production)
- **Encrypted secrets** for sensitive data
- **Schema validation** to ensure configuration correctness
- **Runtime configuration updates** without service restarts
- **Configuration export/import** for backup and migration

### Configuration Loading Order

1. **Default values** (built into the application)
2. **Environment files** (`.env` files)
3. **Environment variables** (system-level overrides)
4. **Runtime modifications** (via CLI or API)

## Environment Setup

### Supported Environments

Atlas supports four main environments:

- **development**: Local development with debug features enabled
- **staging**: Pre-production testing with production-like settings
- **production**: Live deployment with security and performance optimizations
- **testing**: Automated testing environment

### Environment Selection

Set the environment using the `ATLAS_ENVIRONMENT` variable:

```bash
# Set environment
export ATLAS_ENVIRONMENT=production

# Or use environment file
echo "ATLAS_ENVIRONMENT=production" >> config/.env
```

## Configuration Files

### File Structure

```
config/
├── .env                     # Main configuration file
├── development.env          # Development-specific overrides
├── staging.env             # Staging-specific overrides
├── production.env          # Product

*[truncated — see source for full prompt]*