# Dependencies

> This document tracks the project dependencies, their versions, and rationale for inclusion.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Dependencies

This document tracks the project dependencies, their versions, and rationale for inclusion.

## Core Framework

### Next.js 16.0.1

- **Purpose**: React framework with App Router, server components, and built-in optimizations
- **Rationale**: Latest stable version with Turbopack as default bundler, improved performance and explicit caching model
- **Node Version**: Requires Node.js ≥ 20.9
- **Key Features**: Turbopack by default, explicit caching with `revalidateTag(tag, cacheLife)`, layout deduplication, incremental prefetching
- **Breaking Changes**: Async request data access (`params`, `searchParams`, `headers()`, `cookies()`), parallel routes require `default.tsx`

### React 19.2.0 & React DOM 19.2.0

- **Purpose**: UI library with server and client components
- **Rationale**: Latest React version with View Transitions, improved concurrent features and hooks
- **Key Features**: View Transitions API support, `useEffectEvent()` hook, improved server components

### TypeScript 5.x

- **Purpose**: Type-safe JavaScript development
- **Configuration**: Strict mode enabled in tsconfig.json
- **Rationale**: Catches errors at compile time, improves code quality and maintainability

## Database & ORM

### Prisma 6.17.1

- **Purpose**: Next-generation ORM for Node.js and TypeScript
- **Client**: @prisma/client (auto-generated from schema)
- **Rationale**: Type-safe database client with excellent TypeScript support
- **Features**: Migrations, seeding, Prisma Studio GUI

### PostgreSQL 16 (Docker)

- **Purpose**: Production-grade relational database
- **Configuration**: docker-compose.yml with health checks
- **Rationale**: Robust, standards-compliant, excellent JSON support

## Authentication & Authorization

### NextAuth.js 5.0.0-beta.29

- **Purpose**: Authentication for Next.js applications
- **Adapter**: @auth/prisma-adapter (2.11.0)
- **Features**: JWT sessions, OAuth (Google, GitHub), credentials auth
- **Rationale**: Official Next.js authentication so

*[truncated — see source for full prompt]*