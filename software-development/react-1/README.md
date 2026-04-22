# React

> description: Writing React code (React components, React hooks,...) globs: **/use*.?(c|m)[jt]s?(x),**/*.jsx,**/*.tsx,**/*.cjsx,**/*.cjsx,**/*.mjsx,**/*.mtsx,**/use*.js,**/use*.jsx,**/use*.ts,**/use*.tsx,**/use*.cjs,**/use*.cjsx,**/use*.cts,**/use*.ctsx,**/use*.mjs,**/use*.mjsx,**/use*.mts,**/use*.mt

## Tags
`typescript` `react`

## System Prompt
---
description: Writing React code (React components, React hooks,...)
globs: **/use*.?(c|m)[jt]s?(x),**/*.jsx,**/*.tsx,**/*.cjsx,**/*.cjsx,**/*.mjsx,**/*.mtsx,**/use*.js,**/use*.jsx,**/use*.ts,**/use*.tsx,**/use*.cjs,**/use*.cjsx,**/use*.cts,**/use*.ctsx,**/use*.mjs,**/use*.mjsx,**/use*.mts,**/use*.mtsx
alwaysApply: false
---
# React

## Recommended

+ Use functional components exclusively with hooks, define props type with typescript `interface`
+ Keep components pure and focused on single responsibility, decouple the logic from the UI
+ Keep global state minimal, prefer local state and parameter passing when possible
+ Implement lazy loading for all route components
+ Always use `dispatch` function updates for `useState`
+ Should try to use uncontrolled components when possible, only use controlled components when necessary
+ Should always use `memo` (`React.memo`) if applicable. But DO NOT use it for simple components, only use it for components that are expensive to render.
+ Use `useMemo`, `useCallback` for expensive calculations, or when the value is used in another components to prevent unnecessary re-renders. DO NOT use them for simple values or primitives.
+ Use lazy initialization for `useState` for expensive initial values.
+ Avoid introduce side effects (`useEffect`, `useLayoutEffect`,...) as much as possible.
+ Always implement proper cleanup in `useEffect` and `useLayoutEffect` hooks.
+ Avoid using context `useContext` as much as possible.
+ Lazyload components with `lazy` (`React.lazy`) and `Suspense` if applicable.
+ Favor code splitting using dynamic imports for non-critical components and whenever needed.
+ Use `useState` for simple component-level state, `use-mutative` or `useReducer` for complex component-level state.
+ Use `jotai` for global state management, `jotai-mutative` for complex global state management.

## Custom

+ Use `Tanstack React Query`'s `useMutation` for server data mutation, side effects
+ Use `Tanstack React Query`'s `useQu

*[truncated — see source for full prompt]*