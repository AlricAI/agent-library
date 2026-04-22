# DATABASE BACKUP

> This document describes backup and restore procedures for ModPorter-AI's PostgreSQL database.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Database Backup and Restore Guide

This document describes backup and restore procedures for ModPorter-AI's PostgreSQL database.

## Overview

ModPorter-AI uses PostgreSQL with pgvector extension for:
- Conversion job metadata
- User feedback and analytics
- Document embeddings for RAG
- Behavioral testing data

## Backup Methods

### 1. Manual Full Backup

```bash
# Create a full backup of the ModPorter database
pg_dump -h localhost -U postgres -d modporter -Fc -f modporter_backup_$(date +%Y%m%d_%H%M%S).dump

# Or with compression
pg_dump -h localhost -U postgres -d modporter -Fc | gzip > modporter_backup_$(date +%Y%m%d_%H%M%S).sql.gz
```

### 2. Docker Environment Backup

```bash
# Backup from the docker-compose postgres container
docker compose exec postgres pg_dump -U postgres -d modporter -Fc > modporter_backup_$(date +%Y%m%d_%H%M%S).dump

# With compression
docker compose exec postgres pg_dump -U postgres -d modporter | gzip > modporter_backup_$(date +%Y%m%d_%H%M%S).sql.gz
```

### 3. Point-in-Time Recovery (PITR)

For production environments, enable Point-in-Time Recovery:

```bash
# In postgresql.conf (Docker: environment variable)
POSTGRES_INITDB_ARGS: --encoding=UTF-8 --lc-collate=C --lc-ctype=C
# Note: PITR requires WAL archiving configured
```

**Note:** PITR configuration requires:
1. WAL (Write-Ahead Log) archiving to external storage
2. Continuous backup infrastructure
3. Recovery point objective (RPO) configuration

For production, consider using:
- **AWS RDS** with automated backups
- **Supabase** with built-in PITR
- **CloudSQL** with PITR enabled

## Restore Procedures

### 1. Restore from Full Backup

```bash
# Restore to existing database (drops existing data)
pg_restore -h localhost -U postgres -d modporter -c modporter_backup.dump

# Restore to new database
createdb -h localhost -U postgres modporter_new
pg_restore -h localhost -U postgres -d modporter_new modporter_backup.dump
```

### 2. Docker Environment Restore

```bash
# Stop the backe

*[truncated — see source for full prompt]*