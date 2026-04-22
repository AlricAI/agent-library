# Database

> ## Overview

The Octopus Trading Platform uses **PostgreSQL 15** with **TimescaleDB** extension for time-series data optimization. The database is des

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🗄️ Database Schema Documentation - Octopus Trading Platform™

## Overview

The Octopus Trading Platform uses **PostgreSQL 15** with **TimescaleDB** extension for time-series data optimization. The database is designed for high-performance financial data processing with ACID compliance and advanced security features.

## Database Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Application   │    │   TimescaleDB   │    │   Extensions    │
│   Tables        │ -> │   Hypertables   │ -> │   Security      │
│   (OLTP)        │    │   (Time-series) │    │   (Audit/Logs)  │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## Core Tables

### 👥 Users & Authentication

#### `users`
```sql
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    first_name VARCHAR(100),
    last_name VARCHAR(100),
    is_active BOOLEAN DEFAULT true,
    is_verified BOOLEAN DEFAULT false,
    roles TEXT[] DEFAULT ARRAY['user'],
    permissions TEXT[] DEFAULT ARRAY[],
    created_at TIMESTAMPTZ DEFAULT NOW(),
    updated_at TIMESTAMPTZ DEFAULT NOW(),
    last_login_at TIMESTAMPTZ,
    failed_login_attempts INTEGER DEFAULT 0,
    locked_until TIMESTAMPTZ
);
```

#### `api_keys`
```sql
CREATE TABLE api_keys (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    user_id UUID REFERENCES users(id) ON DELETE CASCADE,
    key_hash VARCHAR(64) UNIQUE NOT NULL,
    name VARCHAR(100) NOT NULL DEFAULT 'API Key',
    is_active BOOLEAN DEFAULT true,
    permissions TEXT[] DEFAULT ARRAY[],
    last_used_at TIMESTAMPTZ,
    expires_at TIMESTAMPTZ,
    created_at TIMESTAMPTZ DEFAULT NOW()
);
```

### 💼 Portfolio Management

#### `portfolios`
```sql
CREATE TABLE portfolios (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    user_id UUID REFERENCES users(id) ON DELETE CASCADE,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    total

*[truncated — see source for full prompt]*