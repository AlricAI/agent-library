# Preview Presets

> The icon detail modal lets users preview icons against pre-configured color combinations ("presets") and create their own custom presets.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Preview Presets

The icon detail modal lets users preview icons against pre-configured color combinations ("presets") and create their own custom presets.

## Source of truth

Built-in presets live in **`priv/preview_presets.json`** as an array of objects:

```json
{
  "key": "neon-dark",
  "label": "Neon Dark",
  "color": "#4ade80",
  "bg": "#000000"
}
```

| Field | Description |
|-------|-------------|
| `key` | Stable identifier, kebab-case lowercase. Used as the CSS class name in the "Copy CSS" output and as the localStorage key for the active preset. |
| `label` | Display name shown on the button. Free-form. |
| `color` | Hex color for the icon (the `color`/`fill`/`stroke` value). |
| `bg` | Hex color for the background, OR the literal string `"checker"` for a transparency checkerboard pattern. |

## How it's loaded

The JSON is loaded **at compile time** in `lib/pure_admin_icons_web/live/icon_search_live.ex`:

```elixir
@preview_presets :pure_admin_icons
                 |> :code.priv_dir()
                 |> Path.join("preview_presets.json")
                 |> File.read!()
                 |> Jason.decode!()
@external_resource Path.join(:code.priv_dir(:pure_admin_icons), "preview_presets.json")
```

The `@external_resource` ensures Mix recompiles the LiveView whenever the JSON changes.

## How it's rendered

In the modal template, presets render via a `for` loop:

```heex
<%= for preset <- preview_presets() do %>
  <button data-preset={preset["key"]} style={preset_button_style(preset)}>
    <%= preset["label"] %>
  </button>
<% end %>
```

`preset_button_style/1` generates inline `background-color` + `color` CSS so the buttons preview the actual colors. The checker preset uses a `repeating-conic-gradient` instead.

## How JavaScript reads the same data

The same JSON is passed to the `ColorPicker` JS hook via a `data-presets` attribute on the hook element:

```heex
<div phx-hook="ColorPicker" data-presets={Jason.encode!(preview_presets())} ...>
```

The 

*[truncated — see source for full prompt]*