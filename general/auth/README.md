# Auth

> This project uses [Better Auth](https://www.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Authentication Documentation

This project uses [Better Auth](https://www.better-auth.com/) for authentication, providing secure email/password authentication with session management.

## Overview

Better Auth is a modern, type-safe authentication library that provides:
- Email/password authentication
- Secure session management with httpOnly cookies
- Built-in CSRF protection
- Type-safe API with TypeScript
- Prisma integration for database operations

## Setup

### Environment Variables

Create a `.env` file in the project root with the following variables:

```env
# Database (already configured)
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/mydb"

# Better Auth Configuration
# Generate a secret with: openssl rand -base64 32
BETTER_AUTH_SECRET="your-secret-key-here-minimum-32-characters-long"
BETTER_AUTH_URL="http://localhost:3000"
```

**Important**: The `BETTER_AUTH_SECRET` must be at least 32 characters long and should be kept secure. Never commit this to version control.

### Database Schema

Better Auth requires the following tables:
- `User` - Extended with Better Auth fields (emailVerified, image, createdAt, updatedAt)
- `Session` - Stores user sessions
- `Account` - Stores authentication accounts (email/password, OAuth providers)
- `Verification` - Stores email verification tokens

The schema has been merged with the existing Prisma schema. Run migrations to apply:

```bash
bun run db:migrate
```

## Architecture

### Authentication Flow

```mermaid
sequenceDiagram
    participant User
    participant Client as Auth Client
    participant API as /api/auth/*
    participant Auth as Better Auth
    participant DB as PostgreSQL/Prisma
    participant Proxy as Route Proxy

    User->>Client: Submit Login Form
    Client->>API: POST /api/auth/sign-in/email
    API->>Auth: Process Sign In
    Auth->>DB: Verify Credentials
    DB-->>Auth: User Data
    Auth->>Auth: Create Session
    Auth->>DB: Store Session
    Auth-->>API: Set HttpOnly Cookie
  

*[truncated — see source for full prompt]*