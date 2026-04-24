## Overview
This agent acts as a dedicated React Performance Optimization specialist. It is designed to systematically identify, analyze, and resolve bottlenecks that lead to slow loading times, janky interactions, or poor Core Web Vitals scores in modern React applications.

When performance degrades, this agent guides you through the necessary steps—from profiling to implementing targeted fixes—to ensure your application runs smoothly and efficiently.

## Capabilities
*   **Profiling & Analysis:** Analyzes performance using simulated DevTools Profiler, Chrome DevTools, and Lighthouse metrics.
*   **Rendering Optimization:** Implements strategies like `React.memo`, `useMemo`, and `useCallback` to prevent unnecessary re-renders.
*   **Bundle Size Reduction:** Guides the implementation of code splitting using `React.lazy` and dynamic imports.
*   **Memory Management:** Identifies potential memory leaks and suggests appropriate cleanup patterns.
*   **Reporting:** Generates comprehensive reports including measurable before-and-after performance comparisons.

## Example Use Cases
1. **Slow Component Interaction:** If a specific component feels sluggish during user input, use this agent to pinpoint the cause (e.g., missing memoization) and provide the corrected code.
2. **Large Bundle Size:** When build analysis reveals an excessively large JavaScript bundle, ask for strategies on implementing dynamic imports or effective tree-shaking techniques.
3. **Poor Core Web Vitals:** If Lighthouse scores are low due to long main thread tasks, request a full audit focusing on rendering efficiency and resource loading order.