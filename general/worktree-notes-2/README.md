# Worktree Notes

> Configure `worktree_note_script` to generate initial worktree notes when creating from a PR/MR or issue.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Setting Worktree Notes and Auto-Generated Context

Configure `worktree_note_script` to generate initial worktree notes when creating from a PR/MR or issue. The script receives the selected item's title and body on stdin and can produce multiline output.

<div class="mint-callout">
  <p><strong>Use this page when:</strong> you want to keep clear context per worktree and auto-generate starter notes from PRs or issues.</p>
</div>

## Why notes matter

Worktree notes make it easy to remember context when switching between branches.

A short note can capture:

- what this worktree is for
- what has already been done
- what should happen next

This is especially useful when you return to a worktree after a few days, or when you are juggling multiple PRs in parallel.

## Setting notes manually

Open a worktree and press `i` to edit its note.

Keep the note brief and practical, for example:

```markdown
## Context
- PR: #142
- Goal: finish retry handling in webhook reconciliation

## Next actions
- add failing test for timeout branch
- update retry backoff to cap at 30s
```

## Auto-generating notes with `worktree_note_script`

```yaml
worktree_note_script: "aichat -m gemini:gemini-2.5-flash-lite 'Summarise this ticket into practical implementation notes.'"
```

To store notes in a single synchronisable JSON file rather than git config:

```yaml
worktree_notes_path: ".lazyworktree/notes.json"
```

When `worktree_notes_path` is set, note keys are stored relative to `worktree_dir` instead of absolute filesystem paths, making the file portable across machines and clones.

### Splitted mode

For individual markdown files instead of a single JSON file, use the `splitted` note type. Each worktree note becomes a separate file with YAML frontmatter (icon, color, timestamp) and a markdown body:

```yaml
worktree_note_type: splitted
worktree_notes_path: "~/notes/$REPO_OWNER/$REPO_REPONAME/$WORKTREE_NAME.md"
```

Template variables:

- `$REPO_NAME` — `owner/repo` combined (e.g. `myo

*[truncated — see source for full prompt]*