# ADVANCED USAGE GUIDE

> This guide provides step-by-step instructions for using OOS in different scenarios, ensuring proper project separation in Archon and clear operational procedures.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OOS Usage Guide - Complete Workflows

This guide provides step-by-step instructions for using OOS in different scenarios, ensuring proper project separation in Archon and clear operational procedures.

## 📋 Table of Contents

1. [Quick Start Scenarios](#quick-start-scenarios)
2. [Project Setup Workflows](#project-setup-workflows)
3. [Archon Integration & Project Separation](#archon-integration--project-separation)
4. [Daily Operations](#daily-operations)
5. [Maintenance & Monitoring](#maintenance--monitoring)
6. [Troubleshooting](#troubleshooting)

## 🚀 Quick Start Scenarios

### Scenario 1: Brand New Project
```bash
# 1. Create project directory
mkdir -p /home/ubuntu/dev/my-new-project
cd /home/ubuntu/dev/my-new-project

# 2. Sign into 1Password
eval "$(op signin)"

# 3. Bootstrap with enhanced setup
OP_VAULT="Private" OP_ITEM="bootstrap-env" OP_FIELD="env" \
ORG="YourOrg" VIS="public" \
/home/ubuntu/dev/oos/scripts/bootstrap_enhanced.sh

# 4. Verify setup
./bin/diagnose.sh

# 5. Start monitoring
./bin/health_monitor.sh daemon
```

### Scenario 2: Add OOS to Existing Project
```bash
# 1. Navigate to existing project
cd /path/to/existing-project

# 2. Add OOS as submodule
git submodule add https://github.com/your-org/oos .oos

# 3. Setup OOS in existing project
cd .oos
eval "$(op signin)"
./scripts/scripts/bootstrap_enhanced.sh --project-dir .. --existing-project

# 4. Return to project root and verify
cd ..
./.oos/bin/diagnose.sh
```

### Scenario 3: Team Setup (Multiple Developers)
```bash
# Each developer runs:
git clone https://github.com/your-org/your-project
cd your-project
git submodule update --init --recursive

# Setup individual environment
eval "$(op signin)"  # Each dev uses their own 1Password
cd .oos
./scripts/scripts/bootstrap_enhanced.sh --project-dir .. --user-setup

# Verify team setup
./bin/diagnose.sh --team-mode
```

## 🏗️ Project Setup Workflows

### Creating Different Project Types

#### Web Application Project
```bash
# 1. Create from te

*[truncated — see source for full prompt]*