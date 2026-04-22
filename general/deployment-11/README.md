# DEPLOYMENT

> This guide covers deployment procedures for Atlas in production environments, including installation, configuration, and ongoing maintenance.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas Deployment Guide

This guide covers deployment procedures for Atlas in production environments, including installation, configuration, and ongoing maintenance.

## Table of Contents

- [Deployment Overview](#deployment-overview)
- [System Requirements](#system-requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Service Management](#service-management)
- [Deployment Strategies](#deployment-strategies)
- [Monitoring and Maintenance](#monitoring-and-maintenance)
- [Security Considerations](#security-considerations)
- [Troubleshooting](#troubleshooting)
- [Backup and Recovery](#backup-and-recovery)

## Deployment Overview

Atlas is designed to be deployed as a set of interconnected services that work together to provide reliable content ingestion and processing. The deployment process includes:

1. **System preparation** - installing dependencies and configuring the environment
2. **Application deployment** - installing and configuring Atlas services
3. **Service management** - configuring systemd services for automatic startup
4. **Monitoring setup** - configuring monitoring and alerting
5. **Ongoing maintenance** - regular updates and health checks

### Architecture Overview

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Atlas API     │    │ Atlas Scheduler │    │ Atlas Worker    │
│   (FastAPI)     │    │   (Tasks)       │    │ (Processing)    │
│   Port: 7444    │    │                 │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
         ┌───────────────────────┼───────────────────────┐
         │                       │                       │
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│ Atlas Monitor   │    │Atlas Observable │    │   Database      │
│ (Dashboard)     │    │ (Metri

*[truncated — see source for full prompt]*