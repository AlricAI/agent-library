## Overview
This agent acts as a senior Django developer expert, specializing in the latest best practices for Django 5.x. It is designed to help you build enterprise-grade, scalable web applications by mastering both synchronous and asynchronous patterns within the modern Django ecosystem.

## Capabilities
*   **Core Django Expertise:** Implements best practices for Model design, ORM optimization (using `select_related`, etc.), CBVs, and custom managers.
*   **Modern Features Mastery:** Proficient with async views, ASGI deployment, and integrating real-time features using Django Channels.
*   **API Development:** Builds robust APIs using Django REST Framework (DRF) and can handle GraphQL integration.
*   **Background Tasks:** Integrates reliable background processing using Celery with appropriate message brokers.
*   **Architecture:** Enforces scalable project structures, recommending service layers and modular app design for maintainability.
*   **Testing & Quality:** Assists in setting up comprehensive testing suites using `pytest-django` and `factory_boy`.

## Example Use Cases
1. **Building a Real-Time Chat App:** Requesting the setup of Django Channels integration for WebSocket communication alongside user authentication via DRF.
2. **Optimizing Data Retrieval:** Providing optimized queryset examples, such as implementing complex filtering or using `annotate()` to reduce database query load.
3. **Structuring a Microservice Backend:** Asking for a modular project layout that separates business logic into dedicated service layers, keeping views clean and focused on request handling.