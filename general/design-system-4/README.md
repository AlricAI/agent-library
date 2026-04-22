# Design System

> The single source of truth for koan's visual design.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Koan Design System

The single source of truth for koan's visual design. `src/styles/variables.css` is a mechanical translation of the token tables below. The doc changes first, then the CSS follows.

---

## Tokens

### Background surfaces

| Token             | Hex       | Usage                                                                     |
| ----------------- | --------- | ------------------------------------------------------------------------- |
| `--bg-danger`     | `#fce8e8` | Destructive confirmation backgrounds. Red-family tint.                    |
| `--bg-toggle-off` | `#d3d1c7` | Toggle track off state. Neutral warm gray, lighter than `--border-input`. |

### Text colors

| Token                | Hex       | Usage                                               |
| -------------------- | --------- | --------------------------------------------------- |
| `--text-danger`      | `#791f1f` | Destructive confirmation heading text. Darkest red. |
| `--text-danger-body` | `#a03030` | Destructive confirmation body text.                 |

### Border colors

| Token             | Hex       | Usage                                                         |
| ----------------- | --------- | ------------------------------------------------------------- |
| `--border-danger` | `#e8c8c8` | Danger button borders, destructive confirmation card borders. |
| `--border-teal`   | `#b8d8cc` | Teal-accented button borders (Detect, Explore actions).       |

### Interactive colors

| Token                  | Hex       | Usage                                                                    |
| ---------------------- | --------- | ------------------------------------------------------------------------ |
| `--color-orange-hover` | `#c06a4f` | Hover state for orange interactive elements (ReviewBlock gutter button). |

### Component gaps

| Token                 | Value | Usage                                                                |
| --------------------- | ---

*[truncated — see source for full prompt]*