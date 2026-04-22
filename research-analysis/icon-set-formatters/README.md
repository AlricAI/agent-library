# Icon Set Formatters

> All icon-set-specific identifier generation and package metadata lives in dedicated modules under `lib/pure_admin_icons/icon_sets/`.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Icon Set Formatter Modules

All icon-set-specific identifier generation and package metadata lives in dedicated modules under `lib/pure_admin_icons/icon_sets/`. Each module implements the `PureAdminIcons.IconSets.Formatter` behaviour.

## Structure

```
lib/pure_admin_icons/icon_sets/
├── formatter.ex      # Behaviour + dispatcher (registry)
├── generic.ex        # Fallback for unknown icon sets
├── fluentui.ex       # Microsoft FluentUI System Icons
├── fontawesome.ex    # Font Awesome Free
├── heroicons.ex      # Tailwind Heroicons
├── lucide.ex         # Lucide Icons
└── tabler.ex         # Tabler Icons
```

## Behaviour

```elixir
@callback react_identifier(icon, size :: integer()) :: String.t() | nil
@callback vue_identifier(icon, size :: integer()) :: String.t() | nil
@callback svelte_identifier(icon, size :: integer()) :: String.t() | nil
@callback cssclass_identifier(icon, size :: integer()) :: String.t() | nil

@callback react_package(icon) :: package
@callback vue_package(icon) :: package
@callback svelte_package(icon) :: package
@callback cssclass_package(icon) :: package

@callback react_identifier_sizes(icon) :: [integer()]
@callback vue_identifier_sizes(icon) :: [integer()]
@callback svelte_identifier_sizes(icon) :: [integer()]
```

Where `package` is `{name :: String.t() | nil, npm_url :: String.t() | nil}`.

The `*_identifier_sizes` callbacks return which sizes the modal's per-size loop should iterate. Most icon sets return a single size (the identifier doesn't change with size), but Heroicons React/Vue and FluentUI return all sizes since their import paths or identifiers vary by size.

## Dispatcher

`PureAdminIcons.IconSets.Formatter` provides:

- `for_icon(icon)` / `for_set(code)` — returns the formatter module for a given icon or icon set code
- Top-level helper functions for each callback that route to the right module — e.g., `Formatter.react_identifier(icon, size)` calls `for_icon(icon).react_identifier(icon, size)`

The LiveView calls only 

*[truncated — see source for full prompt]*