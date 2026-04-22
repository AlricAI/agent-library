# Frontmatter Path Timestamps

> ## Problem

When the auto-posting pipeline posts a note to social media and updates it with embed
sections, the modified file may be several hops away

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Frontmatter Path Timestamps: Enveloppe Trail for Obsidian Mobile Publishing

## Problem

When the auto-posting pipeline posts a note to social media and updates it with embed
sections, the modified file may be several hops away from the daily reflection in the
content graph. For example:

```
reflection (today) → reflection (3 days ago) → book (posted & updated)
```

The [Enveloppe](https://github.com/Enveloppe/obsidian-enveloppe) plugin — used to
publish content from Obsidian mobile — discovers changed files using a breadth-first
search strategy similar to our own. It starts from the note you explicitly publish and
follows links to find other changed files. If intermediate files haven't been modified,
Enveloppe won't follow the trail and the posted note (with its new social media embeds)
won't be published.

Manually identifying and publishing all intermediate files from Obsidian mobile is
tedious and error-prone.

## Solution: Updated Frontmatter Trail

After posting a note to social media, update the `updated` property in the YAML
frontmatter of every file along the shortest BFS path from the daily reflection to
the posted note. This creates a breadcrumb trail of modified files that Enveloppe
will follow.

### Example

Given this content graph where `books/deep-book.md` was just posted:

```
reflections/2026-03-10.md → reflections/2026-03-09.md → reflections/2026-03-08.md → books/deep-book.md
```

The pipeline updates the `updated` field in all four files:

```yaml
# reflections/2026-03-10.md
---
updated: 2026-03-10T00:01:08.852Z
---

# reflections/2026-03-09.md
---
updated: 2026-03-10T00:01:08.852Z
---

# reflections/2026-03-08.md
---
updated: 2026-03-10T00:01:08.852Z
---

# books/deep-book.md
---
updated: 2026-03-10T00:01:08.852Z
---
```

Now when the user publishes `reflections/2026-03-10.md` from Obsidian mobile,
Enveloppe's BFS follows the trail of recently-modified files all the way to
`books/deep-book.md`.

## Architecture

### BFS Path Tracking

The exi

*[truncated — see source for full prompt]*