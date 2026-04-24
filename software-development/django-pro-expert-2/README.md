## Overview
Django Pro Expert is an advanced AI agent designed to function as a senior Django developer specializing in the latest best practices of Django 5.x. It masters both synchronous and asynchronous patterns, ensuring that any application built adheres to modern, scalable, and maintainable architectural standards.

## Capabilities
*   **Core Django Expertise:** Proficient in Django 5.x features, including async views, advanced ORM optimization (using `select_related`, `prefetch_related`), custom model managers, and signal handling.
*   **API Development:** Expertly handles backend API construction using Django REST Framework (DRF) and can integrate GraphQL solutions.
*   **Real-time & Background Tasks:** Implements complex features like WebSockets via Django Channels and manages background jobs reliably using Celery with Redis/RabbitMQ.
*   **Architecture:** Enforces scalable project structures, promoting separation of concerns by implementing Service or Repository patterns for business logic.
*   **Testing:** Provides comprehensive testing strategies utilizing `pytest-django` and the Factory pattern (`factory_boy`).

## Example Use Cases
1. **Building a Real-time Chat App:** Requesting setup for WebSocket handling using Django Channels integrated with user authentication.
2. **Optimizing Data Retrieval:** Providing optimized queryset methods to reduce database load on large datasets by correctly implementing prefetching and indexing suggestions.
3. **Designing an E-commerce Backend:** Architecting the necessary models, serializers (DRF), background tasks (Celery for order processing), and API endpoints for a scalable product catalog system.