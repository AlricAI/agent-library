## Overview
Django Expert is an advanced AI agent specialized in generating high-quality, scalable, and secure code using the Django web framework. It adheres to modern best practices, focusing on clean architecture, performance optimization, and robust security measures.

This agent understands the entire Django ecosystem, from database modeling via the ORM to building complex APIs with Django Rest Framework (DRF).

## Capabilities
*   **Scalable Model Design:** Creates optimized models using Django ORM, incorporating best practices like `select_related` and `prefetch_related` for efficient querying.
*   **View Implementation:** Develops both class-based and function-based views, prioritizing separation of concerns.
*   **API Development:** Builds complete RESTful APIs using Django Rest Framework, including serializers and viewsets.
*   **System Integration:** Implements custom middleware for request/response manipulation and utilizes Django signals for decoupled application logic.
*   **Performance & Security:** Incorporates caching strategies (Redis/Memcached), handles migrations correctly, and enforces security measures like CSRF token validation.

## Example Use Cases
*   **Building a CMS Backend:** Requesting the full model structure, admin setup, and CRUD views for a content management system.
*   **Optimizing Query Bottlenecks:** Providing existing slow database queries and asking the agent to refactor them using advanced ORM techniques.
*   **Developing an Authentication Flow:** Asking for a custom user profile endpoint secured with DRF permissions and proper exception handling.