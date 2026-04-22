# Pane Plugin Api

> Lightweight global API exposed in the browser (client only) to let external, retro-style plugins or quick scripts interact with open panes (chat + documents) without importing internal composables.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Pane Plugin API

Lightweight global API exposed in the browser (client only) to let external, retro-style plugins or quick scripts interact with open panes (chat + documents) without importing internal composables.

Global handle:

```ts
// Available after app mounted (dev + prod)
window.__or3PanePluginApi;
```

Type shape (simplified):

```ts
interface PanePluginApi {
    sendMessage(opts: SendMessageOptions): Promise<SendMessageResult>;
    updateDocumentContent(opts: UpdateDocumentOptions): Result;
    patchDocumentContent(opts: PatchDocumentOptions): Result;
    setDocumentTitle(opts: SetDocumentTitleOptions): Result;
    getActivePaneData(): Result<ActivePaneInfo>;
    getPanes(): Result<{ panes: PaneDescriptor[]; activeIndex: number }>;
    posts: {
        create(opts: CreatePostOptions): Promise<Result<{ id: string }>>;
        update(opts: UpdatePostOptions): Promise<Result>;
        listByType(
            opts: ListPostsByTypeOptions
        ): Promise<Result<{ posts: PostData[] }>>;
    };
}
```

`source` is REQUIRED for every call. Use a short stable identifier for your plugin (e.g. `my-plugin`, `bookmarklet`, `ext:foo`). Calls without `source` are rejected.

---

## Accessing the API

```js
const api = window.__or3PanePluginApi;
if (!api) {
    console.warn('Pane plugin API not ready');
}
```

The plugin registers once. If you hot-reload in dev, the same instance is reused.

---

## Pane & Mode Requirements

| Method                | Pane Mode | Requires Thread? | Auto-create Thread?       | Requires Document?    | Notes                          |
| --------------------- | --------- | ---------------- | ------------------------- | --------------------- | ------------------------------ |
| sendMessage           | `chat`    | Yes              | If `createIfMissing:true` | No                    | Creates thread optionally      |
| updateDocumentContent | `doc`     | No               | N/A                       | Yes                   | Full replace     

*[truncated — see source for full prompt]*