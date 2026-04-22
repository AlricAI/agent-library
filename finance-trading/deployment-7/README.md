# Deployment

> ## Overview

This guide covers the complete production deployment of the Octopus Trading Platform, from infrastructure setup to monitoring and mainten

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🚀 Production Deployment Guide - Octopus Trading Platform™

## Overview

This guide covers the complete production deployment of the Octopus Trading Platform, from infrastructure setup to monitoring and maintenance.

## Prerequisites

### System Requirements
- **OS**: Ubuntu 22.04 LTS or RHEL 8+
- **RAM**: 16GB minimum, 32GB recommended
- **Storage**: 500GB SSD minimum, 1TB recommended
- **CPU**: 8 cores minimum, 16 cores recommended
- **Network**: Gigabit internet connection

### Required Software
- Docker 24.0+
- Docker Compose 2.20+
- NGINX 1.20+
- SSL certificates (Let's Encrypt or commercial)
- PostgreSQL 15+ with TimescaleDB
- Redis 7+

## Production Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Load Balancer │    │   API Gateway   │    │   Microservices │
│   (NGINX)       │───▶│   (Kong)        │───▶│   (FastAPI)     │
│   Port 80/443   │    │   Port 8000     │    │   Port 8010     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │   Event Stream  │    │   Database      │
│   (Next.js)     │    │   (Kafka)       │    │   (PostgreSQL)  │
│   Port 3000     │    │   Port 9092     │    │   Port 5432     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## Deployment Methods

### Method 1: Docker Compose (Recommended for Single Server)

#### 1. Server Preparation
```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER

# Install Docker Compose
sudo apt install docker-compose-plugin

# Create application directory
sudo mkdir -p /opt/octopus-trading
sudo chown $USER:$USER /opt/octopus-trading
```

#### 2. Application Setup
```bash
# Clone repository
cd

*[truncated — see source for full prompt]*