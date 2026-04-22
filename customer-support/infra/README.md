# Infra

> ## Application overview: Major components

Genonaut is a multi-tier application consisting of several interconnected services that work together to pr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Infrastructure

## Application overview: Major components

Genonaut is a multi-tier application consisting of several interconnected services that work together to provide content generation, recommendation, and management capabilities.

### Core Components

#### 1. PostgreSQL Database
**Purpose:** Persistent data storage for all application data

**Key responsibilities:**
- Stores users, content items (both regular and auto-generated), tags, interactions, ratings
- Maintains tag hierarchy and relationships via `tag_parents` table
- Tracks content-tag associations in the `content_tags` junction table
- Stores tag cardinality statistics for performance optimization

**Connection:** All backend services connect to PostgreSQL for data persistence

**Configuration:** See `docs/db.md` for schema details and performance optimizations

---

#### 2. Redis
**Purpose:** In-memory data store for caching and message brokering

**Key responsibilities:**
- **Cache layer:** Query result caching (planned for Proposal 2)
- **Message broker:** Celery task queue for asynchronous job processing
- **Session storage:** User session data (if implemented)

**Connection:**
- Backend API connects for caching
- Celery workers connect for task queue management

**Port:** 6379 (default)

---

#### 3. Web API (FastAPI)
**Purpose:** RESTful API server providing all backend functionality

**Key responsibilities:**
- Exposes 77+ REST endpoints for content, tags, users, interactions, recommendations
- Handles authentication and authorization
- Processes business logic and data validation
- Coordinates with Celery for async tasks (image generation, scheduled jobs)

**Technology:** FastAPI (Python), Uvicorn server

**Port:** 8001 (default for local development)

**Startup:** `make api-demo` (uses demo database)

**Stopping/Restarting:** Use environment-specific stop and restart commands rather than manually killing processes:
- `make api-demo-stop` - Stop the demo API server
- `make api-demo-restart

*[truncated — see source for full prompt]*