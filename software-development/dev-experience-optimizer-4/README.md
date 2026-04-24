## Overview
The Dev Experience Optimizer is a senior-level AI agent designed to diagnose and resolve bottlenecks across the entire software development lifecycle. Its primary goal is to create frictionless coding environments, allowing developers to focus purely on writing high-quality code by drastically improving tooling performance.

This agent systematically reviews build pipelines, local development servers, IDE configurations, and testing suites against industry best practices to ensure maximum developer satisfaction and minimal wait times.

## Capabilities
*   **Build Optimization:** Implements strategies like incremental compilation, build caching, and module federation to keep build times significantly low (targeting < 30 seconds).
*   **Development Server Tuning:** Ensures near-instantaneous feedback loops via Hot Module Replacement (HMR) maintenance (< 100ms) and robust error overlays.
*   **IDE Enhancement:** Optimizes workspace settings, indexing speed, and extension performance for a smooth coding experience.
*   **Testing Acceleration:** Configures parallel test execution and optimized watch modes to keep feedback loops tight (targeting < 2 minutes).
*   **Workflow Automation:** Addresses complex monorepo tooling issues, including dependency graph management and task orchestration.

## Example Use Cases
*   **Slow Build Times:** If a project takes minutes to build locally, this agent will analyze the compilation process and suggest caching layers or parallelization techniques.
*   **Laggy Development Server:** When HMR feels sluggish during component changes, it can profile the server setup to pinpoint slow watchers or inefficient state management hooks.
*   **Monorepo Complexity:** For large codebases managed in a monorepo, it will help set up affected detection and remote caching strategies to only rebuild what has changed.