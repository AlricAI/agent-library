# Cursor Rules Agent

> # Instruction to developer: save this file as .cursorrules and place it on the root project directory # Core Principles - Follow **SOLID**, **DRY**, **KISS**, and **YAGNI** principles

## System Prompt
## Instruction to developer: save this file as .cursorrules and place it on the root project directory

## Core Principles
- Follow **SOLID**, **DRY**, **KISS**, and **YAGNI** principles
- Adhere to **OWASP** security best practices
- Break tasks into smallest units and solve problems step-by-step

## Technology Stack
- **Framework**: Kotlin Ktor with Kotlin 2.1.20+
- **JDK**: 21 (LTS)
- **Build**: Gradle with Kotlin DSL
- **Dependencies**: Ktor Server Core/Netty, kotlinx.serialization, Exposed, HikariCP, kotlin-logging, Koin, Kotest

## Application Structure (Feature-Based)
- **Organize by business features, not technical layers**
- Each feature is self-contained with all related components
- Promotes modularity, reusability, and better team collaboration
- Makes codebase easier to navigate and maintain
- Enables parallel development on different features
```
src/main/kotlin/com/company/app/
├── common/              # Shared utilities, extensions
├── config/              # Application configuration, DI
└── features/
    ├── auth/            # Feature directory
    │   ├── models/
    │   ├── repositories/
    │   ├── services/
    │   └── routes/
    └── users/           # Another feature
        ├── ...
```

Test structure mirrors the feature-based organization:
```
src/test/kotlin/com/company/app/
├── common/
└── features/
    ├── auth/
    │   ├── models/
    │   ├── repositories/
    │   ├── services/
    │   └── routes/
    └── users/
        ├── ...
```

## Application Logic Design
1. Route handlers: Handle requests/responses only
2. Services: Contain business logic, call repositories
3. Repositories: Handle database operations
4. Entity classes: Data classes for database models
5. DTOs: Data transfer between layers

## Entities & Data Classes
- Use Kotlin data classes with proper validation
- Define Table objects when using Exposed ORM
- Use UUID or auto-incrementing integers for IDs

## Repository Pattern
```kotlin
interface UserRepository {
    suspend fun

*[truncated — see source for full prompt]*