# Components

> mirroir uses a layered system of **patterns** (declarative — what things look like) and **skills** (imperative — what to do).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Patterns & Skills

mirroir uses a layered system of **patterns** (declarative — what things look like) and **skills** (imperative — what to do). Patterns teach the explorer to recognize UI structure; skills tell it how to execute flows.

| Scale | What it describes | Location |
|-------|------------------|----------|
| **Element patterns** | Row-level UI components (table rows, tab bars, buttons) | `patterns/elements/` |
| **Screen patterns** | Screen archetypes from element composition (dashboard, feed) | `patterns/screens/` |
| **App patterns** | App-level structure, obstacles, skip lists (APP.md) | `patterns/apps/` |
| **Skills** | Step-by-step flows the AI executes | `skills/apps/`, `skills/workflows/` |

Patterns are the atoms (elements), molecules (screens), and organisms (apps) of iOS UI understanding.

## Element Patterns

Element pattern definitions teach the explorer what UI elements look like and how to interact with them. Instead of guessing from raw OCR text, the explorer matches screen regions against pattern definitions — a `.md` file per UI pattern — to decide what to tap, what to skip, and when to backtrack.

### Why Patterns?

Raw OCR returns a flat list of text elements with no structure. A Settings row like `General  >` is two separate elements ("General" and ">") that mean "tappable row that navigates." Without pattern definitions, the explorer must infer this from heuristics that break across apps.

Pattern definitions make this explicit: a `table-row-disclosure` definition says "a row with 1-4 text elements, a chevron, in the content zone — tap the first navigation element, expect navigation, go back after."

## Definition Format

Each component is a `.md` file with YAML front matter and markdown sections:

```markdown
---
version: 1
name: table-row-disclosure
platform: ios
---

# Table Row with Disclosure Indicator

## Description
A standard iOS table row with a right chevron indicating drill-down navigation.

## Visual Pattern
- One or two

*[truncated — see source for full prompt]*