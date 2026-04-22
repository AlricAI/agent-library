# Configuration

> This document describes Genonaut's configuration system, which separates application configuration from deployment secrets and supports multiple deployment environments.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Configuration Management

This document describes Genonaut's configuration system, which separates application configuration from deployment secrets and supports multiple deployment environments.

## Overview

Genonaut uses a two-tier configuration system:
- **JSON config files** - Non-sensitive application configuration (committed to git)
- **.env files** - Sensitive credentials and secrets (excluded from git)

## Directory Structure

```
config/
  base.json                # Shared config across all environments
  local-dev.json           # Local development environment
  local-demo.json          # Local demo environment
  local-test.json          # Local test environment
  cloud-dev.json           # Cloud development environment
  cloud-demo.json          # Cloud demo environment
  cloud-test.json          # Cloud test environment
  cloud-prod.json          # Cloud production environment

env/
  .env.shared              # Shared secrets (passwords, API keys)
  .env.local-dev           # Dev-specific secrets
  .env.local-demo          # Demo-specific secrets
  .env.local-test          # Test-specific secrets
  .env.cloud-dev           # Cloud dev secrets
  .env.cloud-demo          # Cloud demo secrets
  .env.cloud-test          # Cloud test secrets
  .env.cloud-prod          # Cloud prod secrets
  .env                     # Optional: developer overrides (gitignored)
  env.shared.example       # Template for .env.shared
  env.location-type.example # Template for environment-specific files
```

Frontend-specific configuration (for example, UI timeouts or feature toggles) now lives under `frontend/src/config/`. Use the root-level `config/` directory only for backend settings.

## Configuration Load Order

Settings are loaded with the following precedence (lowest to highest):

1. `config/base.json` - Base application config
2. `config/{ENV_TARGET}.json` - Environment-specific config
3. `env/.env.shared` - Shared secrets
4. `env/.env.{ENV_TARGET}` - Environment-specif

*[truncated — see source for full prompt]*