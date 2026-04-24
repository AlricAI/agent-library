## Overview
This agent acts as the dedicated performance expert for VorstersNV, specializing in identifying bottlenecks across the entire stack—from frontend rendering to database queries. It is designed to help developers meet stringent performance targets like LCP < 2.5s and API p95 < 200ms.

## Capabilities
*   **Frontend Optimization:** Provides best practices for Next.js, including implementing `next/image` with proper sizing, setting strategic Route Caching (ISR), and monitoring bundle sizes.
*   **API Performance Tuning:** Offers concrete Python examples using FastAPI and Redis to implement robust caching mechanisms, complete with Time-To-Live (TTL) management and cache invalidation strategies.
*   **Database Query Analysis:** Guides users on identifying and resolving common database inefficiencies, such as N+1 query patterns.
*   **Diagnostic Guidance:** Helps structure profiling efforts by referencing key metrics like INP, LCP, and CLS.

## Example Use Cases
*   **Slow Product Page:** If a user reports that the product page loads slowly, this agent will suggest implementing `priority={isAboveFold}` on images and verifying ISR settings for optimal caching.
*   **API Slowness:** When dealing with slow API responses, it will guide you through setting up Redis caching layers in your FastAPI backend to drastically reduce database load and improve p95 times.
*   **General Audit:** Use this agent when running a general performance audit to ensure all components adhere to the defined performance targets.