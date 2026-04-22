# INSTALL

> This guide provides comprehensive installation instructions for CloudCurio Monorepo, covering fresh installations, upgrades, and various deployment scenarios.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CloudCurio Monorepo — Installation Guide

This guide provides comprehensive installation instructions for CloudCurio Monorepo, covering fresh installations, upgrades, and various deployment scenarios.

## Table of Contents

- [System Requirements](#system-requirements)
- [Fresh Installation](#fresh-installation)
- [Verification Steps](#verification-steps)
- [Configuration](#configuration)
- [Optional Components](#optional-components)
- [Upgrading from Older Versions](#upgrading-from-older-versions)
- [Troubleshooting](#troubleshooting)
- [Platform-Specific Notes](#platform-specific-notes)

## System Requirements

### Minimum Requirements

- **Operating System**: 
  - Linux (Ubuntu 20.04+, Debian 11+, RHEL 8+)
  - macOS 11+ (Big Sur or later)
  - Windows 10/11 with WSL2 (recommended) or native
  
- **Python**: Version 3.10 or higher
  - Check: `python --version` or `python3 --version`
  - With pip and venv modules
  
- **Node.js**: Version 18 or higher (for MCP servers)
  - Check: `node --version`
  - With npm package manager
  
- **Git**: Version 2.30 or higher
  - Check: `git --version`
  
- **Disk Space**: Minimum 500MB free space
  - ~200MB for dependencies
  - ~100MB for virtual environment
  - ~200MB for working data

### Optional Requirements

- **Docker**: Version 20.10+ (for observability stack)
  - Docker Compose v2.0+
  
- **Database**: PostgreSQL 14+ or MySQL 8+ (for certain agents)

## Fresh Installation (Recommended)

This is a **single, ready-to-use** monorepo snapshot that can be used fresh without merging anything.

### Step 1: Prepare Installation Directory

```bash
cd ~/Documents
mkdir -p cloudcurio_monorepo
cd cloudcurio_monorepo
```

### Step 2: Extract or Clone Repository

**Option A: From ZIP Distribution**
```bash
# Unzip this package so you end up with:
# ~/Documents/cloudcurio_monorepo/cloudcurio-monorepo
unzip cloudcurio-monorepo-FINAL.zip -d .
cd cloudcurio-monorepo
```

**Option B: From Git Repository**
```bash
git clone <repository-url

*[truncated — see source for full prompt]*