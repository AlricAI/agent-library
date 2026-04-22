# Error Handling

> Single-page guide to the unified error API.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Error Handling

Single-page guide to the unified error API. Keep this lean; everything here fits on one screen.

## Quick Start

Use `reportError` everywhere instead of raw `console.error`:

```ts
import { reportError, err } from '~/utils/errors';

try {
    await doThing();
} catch (e) {
    reportError(
        err('ERR_INTERNAL', 'Failed to do thing', {
            tags: { domain: 'feature', stage: 'perform', id: item.id },
            retryable: true,
        }),
        {
            toast: true,
            retry: () => doThing(),
        }
    );
}
```

## API Surface (`~/utils/errors.ts`)

| Symbol                                                                                           | Purpose                                                                                         |
| ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| `err(code, message, { severity?, retryable?, tags?, cause? })`                                   | Factory creating a typed `AppError`.                                                            |
| `isAppError(v)` / `asAppError(v, fb?)`                                                           | Type guard / coercion with fallback code & message.                                             |
| `reportError(input, { code?, message?, tags?, toast?, silent?, retry?, severity?, retryable? })` | Normalize, scrub, dedupe-log, emit hooks, optionally toast & surface retry. Returns `AppError`. |
| `simpleRetry(fn, attempts=2, delayMs=400)`                                                       | Minimal linear async retry helper.                                                              |
| `useErrorToasts()`                                                                               | Deprecated noop shim (avoid; kept for legacy components).                                       |


*[truncated — see source for full prompt]*