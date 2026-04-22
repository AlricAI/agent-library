# API REFERENCE

> This reference provides comprehensive documentation for all OOS tools, their commands, options, and integration patterns.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OOS API Reference - Complete Tool Documentation

This reference provides comprehensive documentation for all OOS tools, their commands, options, and integration patterns.

## 📋 Table of Contents

1. [Bootstrap System](#bootstrap-system)
2. [Diagnostics System](#diagnostics-system)
3. [Health Monitoring](#health-monitoring)
4. [Testing Framework](#testing-framework)
5. [Template Management](#template-management)
6. [Performance Monitoring](#performance-monitoring)
7. [Security Auditing](#security-auditing)
8. [MCP Management](#mcp-management)
9. [Key Rotation](#key-rotation)
10. [Web Dashboard API](#web-dashboard-api)

## 🚀 Bootstrap System

### `scripts/bootstrap_enhanced.sh`

Enhanced bootstrap script with comprehensive project setup capabilities.

#### Usage
```bash
./scripts/scripts/bootstrap_enhanced.sh [PROJECT_NAME] [PROJECT_DIR] [OPTIONS]
```

#### Options
| Option | Description | Example |
|--------|-------------|---------|
| `--dry-run` | Preview changes without executing | `--dry-run` |
| `--force` | Force overwrite existing configuration | `--force` |
| `--skip-deps` | Skip dependency checking | `--skip-deps` |
| `--existing-project` | Setup OOS in existing project | `--existing-project` |
| `--project-dir DIR` | Specify project directory | `--project-dir /path/to/project` |
| `--template TYPE` | Use specific template setup | `--template web-app` |
| `--security-hardened` | Apply enhanced security settings | `--security-hardened` |
| `--user-setup` | Individual developer setup | `--user-setup` |
| `--reset-config` | Reset to default configuration | `--reset-config` |
| `--verbose` | Show detailed output | `--verbose` |
| `--help` | Show help information | `--help` |

#### Environment Variables
| Variable | Description | Default |
|----------|-------------|---------|
| `OP_VAULT` | 1Password vault name | `Private` |
| `OP_ITEM` | 1Password item name | `bootstrap-env` |
| `OP_FIELD` | 1Password field name | `env` |
| `ORG` | GitHub organization | Requir

*[truncated — see source for full prompt]*