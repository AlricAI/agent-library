# Database

> This project uses [Prisma ORM](https://www.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Database Setup Guide

This project uses [Prisma ORM](https://www.prisma.io/) for database access and management.

## Overview

Prisma provides a type-safe database client with automatic migrations, schema management, and excellent TypeScript support. The setup uses PostgreSQL by default, but can be configured for other databases.

## Prerequisites

- A PostgreSQL database (local or cloud)
- Node.js/Bun runtime
- Environment variables configured
- Docker and Docker Compose (optional, for local development)

## Quick Start with Docker Compose

The easiest way to get started is using the included Docker Compose setup:

1. **Start PostgreSQL**:
   ```bash
   bun run docker:up
   ```

2. **Wait for database to be ready** (takes a few seconds on first run)

3. **Run migrations**:
   ```bash
   bun run db:migrate
   ```

4. **Seed the database** (optional):
   ```bash
   bun run db:seed
   ```

The database will be available at `localhost:5432` with:
- **User**: `postgres`
- **Password**: `postgres`
- **Database**: `mydb`

### Docker Commands

- `bun run docker:up` - Start PostgreSQL container
- `bun run docker:down` - Stop PostgreSQL container
- `bun run docker:logs` - View PostgreSQL logs
- `bun run docker:restart` - Restart PostgreSQL container

To stop and remove the database (data will persist in volume):
```bash
bun run docker:down
```

To remove the database and all data:
```bash
docker-compose down -v
```

## Environment Variables

Create a `.env` file in the project root (use `.env.example` as a template):

```env
DATABASE_URL="postgresql://user:password@localhost:5432/mydb?schema=public"
```

### Connection String Formats

- **PostgreSQL**: `postgresql://user:password@host:port/database?schema=public`
- **MySQL**: `mysql://user:password@host:port/database`
- **SQLite**: `file:./dev.db`
- **MongoDB**: `mongodb://user:password@host:port/database`

## Installation

Dependencies are already installed. If you need to reinstall:

```bash
bun install
```

## Database 

*[truncated — see source for full prompt]*