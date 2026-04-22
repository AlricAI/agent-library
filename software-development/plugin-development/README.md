# Plugin Development

> Hulunote provides a plugin system that lets you extend the outliner with custom components, styles, and JavaScript logic.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Hulunote Plugin Development Guide

Hulunote provides a plugin system that lets you extend the outliner with custom components, styles, and JavaScript logic. Plugins are managed entirely from within Hulunote itself — no need to edit HTML or config files.

## Table of Contents

- [How Plugins Are Loaded](#how-plugins-are-loaded)
- [Code Blocks with CodeMirror](#code-blocks-with-codemirror)
- [Plugin API Reference](#plugin-api-reference)
- [Writing a Custom Renderer](#writing-a-custom-renderer)
- [RenderContext](#rendercontext)
- [Lifecycle Hooks](#lifecycle-hooks)
- [Full Example: Minimal Plugin](#full-example-minimal-plugin)
- [Official Example Plugin](#official-example-plugin)

---

## How Plugins Are Loaded

Plugins are loaded through two **special notes** in your database:

### `hulunote/javascript`

Create a note with the title `hulunote/javascript`. Each **child block** is one JavaScript entry.

Three formats are supported:

**1. URL (loaded as `<script src="...">`)**

```
/plugins/hulunote-kanban-table-plugin.js
```

**2. Inline code (executed directly)**

```
console.log("hello from inline JS")
```

**3. Fenced code block with CodeMirror editor (recommended for inline code)**

    ```js
    window.HulunotePlugin.register({
      name: 'my-plugin',
      version: '1.0.0',
      renderers: {
        greeting: function(ctx) {
          ctx.container.innerHTML = '<div>Hello!</div>';
        }
      }
    });
    ```

When a block uses ``` fences, the code is displayed in a full **CodeMirror editor** with syntax highlighting, line numbers, and editable in place. The ``` fences are automatically stripped before execution.

### `hulunote/css`

Create a note with the title `hulunote/css`. Each **child block** is one CSS entry. Same three formats:

    ```css
    .my-custom-class {
      color: #6c8dfa;
      font-weight: bold;
    }
    ```

### Loading Timing

Plugins are loaded automatically after the database finishes syncing (all notes and blocks are in memory).

*[truncated — see source for full prompt]*