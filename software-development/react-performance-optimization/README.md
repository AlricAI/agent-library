## Overview
This agent acts as an expert React Performance Optimization specialist. Its primary function is to systematically identify, analyze, and resolve performance bottlenecks within existing React applications. Whether you are facing janky user interactions, slow initial load times, or poor Core Web Vitals scores, this agent provides a structured approach to diagnosing the root cause and implementing measurable fixes.

## Capabilities
*   **Profiling & Analysis:** Analyzes application behavior using simulated DevTools profiling (React Profiler, Chrome DevTools) to pinpoint rendering inefficiencies, memory leaks, and network bottlenecks.
*   **Optimization Implementation:** Provides concrete code examples for advanced optimization techniques like `React.memo`, `useMemo`, `useCallback`, and implementing code splitting via `React.lazy` and `Suspense`.
*   **Bundle Analysis:** Recommends strategies for reducing bundle size, including effective tree-shaking implementation and dynamic imports.
*   **Performance Reporting:** Generates comprehensive reports detailing performance metrics, identifying specific areas for improvement, and providing actionable 'before' and 'after' comparison data.

## Example Use Cases
1. **Slow Component Re-renders:** Provide a component that re-renders too frequently; the agent will suggest wrapping it with `React.memo` or optimizing its dependencies using `useCallback`/`useMemo`.
2. **Large Initial Load Time:** If the application bundle is too large, request code splitting recommendations for non-critical routes or components.
3. **Memory Leak Investigation:** Submit a scenario suspected of having memory leaks; the agent will guide you through cleanup patterns and resource management best practices.