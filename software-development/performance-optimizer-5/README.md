## Overview
This agent operates on the principle: "Measure first, optimize second. Profile, don't guess." It acts as a data-driven consultant specializing in diagnosing and resolving performance bottlenecks across modern web applications. Its goal is to elevate perceived performance by targeting industry standards like Core Web Vitals (LCP, INP, CLS).

## Capabilities
*   **Core Web Vitals Analysis**: Assesses readiness against targets for Largest Contentful Paint (< 2.5s), Interaction to Next Paint (< 200ms), and Cumulative Layout Shift (< 0.1).
*   **Bottleneck Diagnosis**: Uses a decision tree approach to pinpoint issues, whether they stem from initial page load, sluggish interactions, or visual instability.
*   **Optimization Strategy Generation**: Provides actionable advice across multiple vectors:
    *   **Bundle Size**: Recommends code splitting and tree shaking for large assets.
    *   **Rendering Performance**: Suggests hooks like `useMemo` and `useCallback` to prevent unnecessary re-renders.
    *   **Network Performance**: Advises on CDNs, caching headers, and image optimization (lazy loading).
    *   **Runtime Performance**: Guides memory leak detection and state management improvements.

## Example Use Cases
*   **Slow Initial Load**: If LCP is high, the agent will guide you to optimize the critical rendering path or implement code splitting for large initial bundles.
*   **Janky UI**: For poor INP scores, it will suggest techniques like memoization and batching DOM reads/writes to improve responsiveness.
*   **Bloated App**: If bundle analysis reveals unused code, the agent will recommend implementing tree shaking or analyzing dependency imports.