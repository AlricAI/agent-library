# REMOTE STAGING DEPLOYMENT

> This guide provides step-by-step instructions for deploying CodeFRAME to a centralized staging server instead of running it locally.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Remote Staging Server Deployment Guide

This guide provides step-by-step instructions for deploying CodeFRAME to a centralized staging server instead of running it locally.

## Server Configuration

Before starting, create your server configuration file:

```bash
# In your local codeframe directory
cp .staging-server.conf.example .staging-server.conf
nano .staging-server.conf
```

Fill in your actual server details:
```bash
STAGING_SERVER_HOST="your-server-hostname"
STAGING_SERVER_USER="your-username"
STAGING_FRONTEND_PORT="14100"
STAGING_BACKEND_PORT="14200"
```

**Note**: `.staging-server.conf` is gitignored and contains your private server details.

Throughout this guide:
- `YOUR_STAGING_SERVER` = your server hostname
- `YOUR_USER` = your SSH username
- Replace these placeholders with your actual values or use the environment variables from `.staging-server.conf`

---

## Prerequisites

Before starting, ensure you have:

1. **SSH access** to your staging server
2. **Git installed** on the remote server
3. **API Keys** (ANTHROPIC_API_KEY, optionally OPENAI_API_KEY)
4. **Network access** to ports 14100 (frontend) and 14200 (backend) on the remote server

---

## Part 1: Initial Server Setup (One-Time)

### Step 1.1: Connect to Remote Server

```bash
# From your local machine
ssh YOUR_USER@YOUR_STAGING_SERVER
```

### Step 1.2: Install System Dependencies

```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Install Node.js and npm (required for PM2 and frontend)
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs

# Verify Node.js installation
node --version  # Should show v20.x or higher
npm --version   # Should show 10.x or higher

# Install Python 3.11+ (if not already installed)
sudo apt install -y python3.11 python3.11-venv python3-pip

# Install uv (fast Python package manager)
curl -LsSf https://astral.sh/uv/install.sh | sh
source ~/.bashrc  # Reload shell to get uv in PATH

# Verify uv install

*[truncated — see source for full prompt]*