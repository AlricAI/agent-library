# Igniter.js: Core Architecture

> description: | Provides a high-level overview of the Igniter.js core architecture, its integration with the Next.js App Router, the feature-based API structure, and the universal type-safe client. alwaysApply: true

## Tags
`typescript` `react` `redis`

## System Prompt
---
description: |
  Provides a high-level overview of the Igniter.js core architecture, its integration with the Next.js App Router, the feature-based API structure, and the universal type-safe client.
alwaysApply: true
---

# Igniter.js: Core Architecture

This document outlines the foundational architecture of an Igniter.js application when integrated with the Next.js App Router.

## 1. Core Architectural Principles

The application leverages the Next.js App Router to execute code on both the server (React Server Components, API Routes) and the client (Client Components). Igniter.js is integrated as a structured, type-safe API layer that sits within the Next.js project.

### 1.1. API Entry Point: The Bridge
All API requests are funneled through the main Express application, which acts as a bridge to the Igniter.js backend.

-   **File Location**: `src/index.ts`
-   **Mechanism**: This file uses the `expressAdapter` to integrate the Igniter.js router with Express. It translates incoming Express requests into a format Igniter.js can process and translates Igniter.js responses back into a format Express can serve. It handles all HTTP methods (`GET`, `POST`, etc.) for any route matching the `IGNITER_API_BASE_PATH` (e.g., `/api/v1/*`). You will rarely need to modify this file.

### 1.2. API Layer: Feature-Based Structure
All backend business logic is organized using a **Feature-Based Architecture** within the `src/features` directory.

-   `src/igniter.ts`: The central configuration file where the `igniter` instance is created. This is where global plugins and adapters are registered.
-   `src/igniter.router.ts`: This file assembles the main `AppRouter` by importing and registering all feature controllers. It serves as the **single source of truth** for your API's structure and endpoints.
-   `src/features/[feature]/controllers/`: This is where your business logic resides. Each controller defines a set of related API `actions` (`query`, `mutation`).

### 1.3. The Univ

*[truncated — see source for full prompt]*