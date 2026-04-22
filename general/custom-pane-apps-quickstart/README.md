# Custom Pane Apps Quickstart

> Custom Pane Apps allow plugins to register arbitrary Vue components that render in the multi-pane workspace alongside chat and document panes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Custom Pane Apps - Quick Start

Custom Pane Apps allow plugins to register arbitrary Vue components that render in the multi-pane workspace alongside chat and document panes. Data is persisted in the `posts` table with custom `postType` values.

## Basic Setup

### 1. Create a Nuxt Plugin

Plugins are auto-registered from `app/plugins/`. Create a `.client.ts` file for client-only code:

```typescript
// app/plugins/my-custom-app.client.ts
export default defineNuxtPlugin(async () => {
    if (!process.client) return;

    const { registerPaneApp } = usePaneApps();
    const { registerSidebarPage } = await import(
        '~/composables/sidebar/registerSidebarPage'
    );

    // Your registration code here...
});
```

### 2. Register a Pane App

```typescript
registerPaneApp({
    id: 'my-app', // Unique identifier (becomes pane mode)
    label: 'My App', // Display name
    icon: 'pixelarticons:note', // Icon name
    component: MyPaneComponent, // Vue component
    postType: 'my-app-data', // Optional: post type for persistence
    createInitialRecord: async () => {
        // Optional: Create initial record when opening new pane
        const api = (globalThis as any).__or3PanePluginApi;
        const result = await api.posts.create({
            postType: 'my-app-data',
            title: 'New Item',
            content: '',
            meta: {
                /* custom data */
            },
            source: 'my-plugin',
        });

        if (!result.ok) throw new Error(result.message);
        return { id: result.id };
    },
});
```

### 3. Create Your Pane Component

Your component receives these props:

```typescript
import { defineComponent } from 'vue';

const MyPaneComponent = defineComponent({
    name: 'MyPane',
    props: {
        paneId: { type: String, required: true },
        recordId: { type: String, default: null }, // Post ID
        postType: { type: String, required: true },
        postApi: { type: Object, required: true }, // CRUD h

*[truncated — see source for full prompt]*