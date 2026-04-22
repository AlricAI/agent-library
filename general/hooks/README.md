# Hooks

> A lightweight, type-safe hook engine for the Nuxt frontend.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Hook/Action System for Nuxt

A lightweight, type-safe hook engine for the Nuxt frontend. It lets components, composables, and plugins subscribe to events (actions) or transform data (filters) with predictable ordering and SSR/HMR safety.

-   Actions: fire-and-forget side effects (logging, analytics, UI updates)
-   Filters: transform values in a pipeline (value-in → value-out)
-   Priorities: lower runs earlier (default 10)
-   Wildcards: use `*` to match patterns, e.g. `ui.*:action:after`

## Installation & Access

The engine is provided globally by Nuxt plugins:

-   Client: singleton instance across HMR
-   Server (SSR): fresh instance per request

Access anywhere:

```ts
import { useNuxtApp } from '#app';

const hooks = useNuxtApp().$hooks;
// or
import { useHooks } from '~/app/composables/useHooks';
const hooks2 = useHooks();
```

In components, prefer the lifecycle-safe composable:

```ts
import { useHookEffect } from '~/app/composables/useHookEffect';

useHookEffect('route.change:action:after', (_ctx, to, from) => {
    console.log('navigated from', from, 'to', to);
});
```

## API Overview

Engine methods:

-   Filters
    -   addFilter(name, fn, priority?, acceptedArgs?)
    -   removeFilter(name, fn, priority?)
    -   applyFilters(name, value, ...args) => Promise<Return>
    -   applyFiltersSync(name, value, ...args)
-   Actions
    -   addAction(name, fn, priority?, acceptedArgs?)
    -   removeAction(name, fn, priority?)
    -   doAction(name, ...args) => Promise<void>
    -   doActionSync(name, ...args)
-   Utils
    -   hasFilter(name?, fn?) => boolean|priority
    -   hasAction(name?, fn?) => boolean|priority
    -   removeAllCallbacks(priority?)
    -   currentPriority() => number|false
-   Ergonomics
    -   onceAction(name, fn, priority?)
    -   on(name, fn, { kind: 'action'|'filter', priority }) → disposer
    -   off(disposer)

Types are exported from `app/utils/hooks`.

## Hook Naming

Use hierarchical strings with dots/colons to keep hooks

*[truncated — see source for full prompt]*