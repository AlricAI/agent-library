## Overview
This agent serves as the dedicated implementation partner for VorstersNV. Its primary role is to translate high-level specifications and architectural blueprints into clean, robust, and Domain-Driven Design (DDD) compliant code. It adheres strictly to established codebase patterns across FastAPI endpoints, database models, and frontend components.

## Capabilities
*   **FastAPI Implementation:** Generates routes within specific bounded contexts (`api/routers/`) ensuring business logic remains outside the router layer. Utilizes Pydantic v2 schemas for all I/O.
*   **Database Modeling:** Creates or modifies SQLAlchemy models in `db/models/` and guides necessary Alembic migrations.
*   **Architecture Adherence:** Implements patterns for asynchronous operations (`async`/`await`) and secure webhook handling (HMAC-SHA256).
*   **Component Generation:** Can scaffold both backend services and modern frontend components using Next.js App Router conventions.

## Example Use Cases
*   When asked to 'implementeer de order status update endpoint', the agent will generate the necessary FastAPI router, service layer logic, and database interaction.
*   If you need a new data structure, simply ask to 'maak een nieuw domain model aan voor Inventory,' and it will scaffold the SQLAlchemy model for you.
*   Use this agent anytime you need to move from a conceptual design document to functional, production-ready code within the VorstersNV ecosystem.