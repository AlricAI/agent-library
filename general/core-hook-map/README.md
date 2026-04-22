# Core Hook Map

> This document provides a comprehensive reference of all core hooks available in the application.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Core Hook Map

This document provides a comprehensive reference of all core hooks available in the application. Hooks are the primary extension mechanism, allowing plugins to observe events (actions) or transform data (filters) without modifying core code.

## Hook Types

-   **Actions**: Fire-and-forget side effects (logging, analytics, UI updates)
-   **Filters**: Transform values in a pipeline (value-in → value-out)

## Veto Semantics

Some filters support veto behavior:

-   Returning `false` cancels the operation
-   Returning an empty string `''` may clear or skip the operation (context-dependent)
-   Filters are always chainable — each receives the output of the previous

## Priority

-   Lower priority runs earlier (default 10)
-   Use priority to control hook execution order
-   Equal priorities preserve insertion order

## Chat & Message Lifecycle

### Outgoing Message

**`ui.chat.message:filter:outgoing`** (filter)

-   **Phase**: Before user message is appended to thread
-   **Input**: `text: string`
-   **Return**: `string | false`
-   **Veto**: `false` or empty string skips append and network call
-   **Use cases**: Input sanitization, content moderation, text preprocessing

### Model Selection

**`ai.chat.model:filter:select`** (filter)

-   **Phase**: Before sending request to AI
-   **Input**: `modelId: string`
-   **Return**: `string` (model ID to use)
-   **Use cases**: Override model selection, A/B testing

### Message Transform

**`ai.chat.messages:filter:input`** (filter)

-   **Phase**: Before messages sent to AI
-   **Input**: `messages: any[]`
-   **Return**: `any[]`
-   **Use cases**: Context injection, prompt engineering

### Send Lifecycle

**`ai.chat.send:action:before`** (action)

-   **Phase**: Before streaming starts
-   **Payload**: `AiSendBefore { threadId?, modelId, user: { id, length }, assistant: { id, streamId }, messagesCount? }`
-   **Use cases**: Track send events, analytics

**`ai.chat.send:action:after`** (action)

-   **

*[truncated — see source for full prompt]*