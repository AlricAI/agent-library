# SETUP GUIDE

> Complete setup guide for deploying OOS with Agent-OS integration on OCI free tier.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🚀 OOS Agent-OS Setup Guide

Complete setup guide for deploying OOS with Agent-OS integration on OCI free tier.

## Quick Start (3 Commands)

```bash
# 1. Bootstrap the system
make -C ops bootstrap

# 2. Configure environment
cp ops/.env.template ops/.env && $EDITOR ops/.env

# 3. Initialize and check health
sqlite3 /opt/oos/data/oos.db < ops/schema.sql && make -C ops start
```

## Prerequisites

### System Requirements
- Ubuntu 20.04+ or similar Linux distribution
- 1GB RAM minimum (OCI free tier: VM.Standard.E2.1.Micro)
- 10GB storage minimum (OCI free tier: 200GB block volume)
- SSH access with key-based authentication

### Required Tools
```bash
# Install on Ubuntu/Debian
sudo apt-get update
sudo apt-get install -y sqlite3 python3-pip curl jq

# Install Python tools
pip3 install --user datasette sqlite-web

# Install security tools
make -C ops install-sops
```

## Step-by-Step Setup

### 1. Initial System Setup

```bash
# Create OOS user (recommended)
sudo useradd -m -s /bin/bash oos
sudo usermod -aG sudo oos

# Create directory structure
sudo mkdir -p /opt/oos/{data,backups,config}
sudo chown -R oos:oos /opt/oos

# Clone OOS repository
sudo -u oos git clone https://github.com/Khamel83/oos.git /opt/oos/repo
cd /opt/oos/repo
```

### 2. Environment Configuration

```bash
# Copy and edit environment template
cp ops/.env.template ops/.env

# Essential configuration variables:
cat >> ops/.env << 'EOF'
# Paths
OOS_DB=/opt/oos/data/oos.db
OOS_DATA_ROOT=/opt/oos/data
OOS_BACKUP_DIR=/opt/oos/backups

# Security
SOPS_AGE_KEY_FILE=/opt/oos/config/age-key.txt

# Google Sheets (optional but recommended)
GOOGLE_SERVICE_ACCOUNT_JSON=/opt/oos/config/service-account.json
GOOGLE_SPREADSHEET_ID=your_spreadsheet_id_here

# Monitoring (optional)
TELEGRAM_BOT_TOKEN=your_bot_token_here
TELEGRAM_CHAT_ID=your_chat_id_here
EOF
```

### 3. Database Initialization

```bash
# Initialize SQLite database
mkdir -p /opt/oos/data
sqlite3 /opt/oos/data/oos.db < ops/schema.sql

# Verify initial

*[truncated — see source for full prompt]*