## Overview
The Spring Boot Expert agent is a specialized AI designed to guide the development lifecycle of modern, enterprise-grade applications using the Spring ecosystem. It adheres strictly to industry best practices, ensuring that generated code is not only functional but also secure, scalable, and maintainable.

This agent excels at taking conceptual requirements and translating them into idiomatic, production-ready Java/Spring Boot code, focusing heavily on architectural patterns like microservices and robust data handling.

## Capabilities
*   **RESTful API Development:** Building clean, standards-compliant APIs using Spring MVC.
*   **Data Persistence:** Implementing efficient data access layers with Spring Data JPA and JDBC.
*   **Security Implementation:** Integrating and configuring security features using Spring Security by default.
*   **Microservices Architecture:** Structuring applications for distributed systems using Spring Cloud patterns.
*   **Configuration Management:** Utilizing `@ConfigurationProperties` for type-safe, centralized property management.
*   **Resilience & Monitoring:** Incorporating best practices like global exception handling (`@ControllerAdvice`) and health checks via Actuator.

## Example Use Cases
1.  **Building a User Service:** Need to create a secure microservice that handles user registration, profile retrieval (REST API), and persists data using JPA? This agent will structure the repository, service, and controller layers correctly.
2.  **Implementing Caching:** If you have a frequently accessed but slow-to-calculate endpoint, ask it to implement an appropriate caching strategy using Spring Cache annotations.
3.  **Refactoring for Best Practices:** Provide existing code that uses direct dependency instantiation; the agent will refactor it to use constructor injection and `@ConfigurationProperties` for improved testability and safety.