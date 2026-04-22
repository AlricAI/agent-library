# TROUBLESHOOTING

> This guide provides solutions for common issues, diagnostic procedures, and recovery methods for the OOS system.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OOS Troubleshooting Guide

This guide provides solutions for common issues, diagnostic procedures, and recovery methods for the OOS system.

## 🚨 Emergency Quick Fixes

### System Completely Broken
```bash
# Stop all processes
pkill -f health_monitor
pkill -f key_rotator
pkill -f performance_monitor

# Reset to clean state
./scripts/scripts/bootstrap_enhanced.sh --reset-config --force

# Verify basic functionality
./bin/diagnose.sh --self-heal
```

### Can't Access 1Password
```bash
# Sign in again
eval "$(op signin)"

# Verify access
op item get "bootstrap-env" --vault "Private" --fields env

# If still failing, check account
op account list
op account use <account>
```

### Archon MCP Unreachable
```bash
# Check local Archon
curl -I http://localhost:8051/mcp

# If fails, try remote
export ARCHON_URL=https://archon.khamel.com:8051/mcp
curl -I $ARCHON_URL

# Update environment
echo "ARCHON_URL=$ARCHON_URL" >> .env
```

## 🔍 Common Issues & Solutions

### 1. Bootstrap Failures

#### Issue: "Dependencies missing"
```bash
# Symptoms
./scripts/scripts/bootstrap_enhanced.sh
ERROR: Required dependency not found: op

# Solution
# Install 1Password CLI
curl -sSfLo op.zip https://cache.agilebits.com/dist/1P/op2/pkg/v2.21.0/op_linux_amd64_v2.21.0.zip
unzip op.zip && sudo mv op /usr/local/bin/
op --version
```

#### Issue: "1Password authentication failed"
```bash
# Symptoms
OP authentication failed (exit code: 1)

# Diagnosis
op account list
eval "$(op signin)"

# Solutions
# 1. Sign in to correct account
op signin --account <your-account>

# 2. Check item exists
op item get "bootstrap-env" --vault "Private"

# 3. Verify field name
op item get "bootstrap-env" --vault "Private" --fields env
```

#### Issue: "Network connectivity issues"
```bash
# Symptoms
Failed to connect to github.com:443

# Diagnosis
./bin/diagnose.sh --check-network

# Solutions
# 1. Check internet connection
ping -c 3 8.8.8.8

# 2. Check DNS resolution
nslookup github.com

# 3. Check firewall/proxy
cu

*[truncated — see source for full prompt]*