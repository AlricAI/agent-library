# PRODUCTION DEPLOYMENT

> **Version:** 1.0
**Date:** August 24, 2025
**Target:** Production-ready deployment of Atlas content processing system

## Table of Contents

1. [Prere

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas Production Deployment Guide

**Version:** 1.0
**Date:** August 24, 2025
**Target:** Production-ready deployment of Atlas content processing system

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Infrastructure Requirements](#infrastructure-requirements)
3. [Deployment Options](#deployment-options)
4. [Step-by-Step Deployment](#step-by-step-deployment)
5. [Configuration Management](#configuration-management)
6. [Security Hardening](#security-hardening)
7. [Monitoring & Alerting](#monitoring--alerting)
8. [Backup & Recovery](#backup--recovery)
9. [Performance Tuning](#performance-tuning)
10. [Troubleshooting](#troubleshooting)

## Prerequisites

### System Requirements

**Minimum Production Requirements:**
- **OS:** Ubuntu 20.04 LTS / CentOS 8 / RHEL 8
- **CPU:** 4 cores (8+ recommended)
- **RAM:** 16GB (32GB+ recommended for large datasets)
- **Storage:** 500GB SSD (1TB+ recommended)
- **Network:** Stable internet connection with firewall access

**Recommended Production Specifications:**
- **CPU:** 8+ cores with high clock speed
- **RAM:** 32GB+ for handling large content collections
- **Storage:** NVMe SSD with 2TB+ capacity
- **Network:** Redundant network connections

### Software Dependencies

**Required Software:**
```bash
# System packages
sudo apt update && sudo apt install -y \
    python3.9 python3.9-venv python3-pip \
    postgresql postgresql-contrib \
    nginx redis-server supervisor \
    git curl wget unzip \
    build-essential libffi-dev libssl-dev \
    libpq-dev python3-dev

# Optional but recommended
sudo apt install -y \
    htop iotop netstat-nat \
    logrotate fail2ban ufw \
    certbot python3-certbot-nginx
```

## Infrastructure Requirements

### Database Configuration

**PostgreSQL Setup (Recommended for Production):**
```bash
# Install and configure PostgreSQL
sudo postgresql-setup --initdb
sudo systemctl start postgresql
sudo systemctl enable postgresql

# Create Atlas database and user
sudo -u postgres psql << EOF


*[truncated — see source for full prompt]*