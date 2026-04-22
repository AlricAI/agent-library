# Update

> Update commands and agents from the source repository

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
You are helping the user update their installed commands and agents from the source repository. Parse arguments from `$ARGUMENTS` and follow each step in order.

## Step 1: Parse Arguments

Extract flags from `$ARGUMENTS`:

- `--dry-run` → preview changes only, do not modify files
- `--prune` → remove orphaned files not present in source
- `--force` → update even if already at latest version
- `--source <path|url>` → custom source (local path or git URL)

**Defaults:**

```bash
DRY_RUN=false
PRUNE=false
FORCE=false
SOURCE="https://github.com/rlajous/claude-code-commands.git"
```

## Step 2: Detect Project Root

Find the project root by locating the `.claude/` directory:

```bash
# Walk up from current directory to find .claude/
DIR="$(pwd)"
while [ "$DIR" != "/" ]; do
  if [ -d "$DIR/.claude" ]; then
    echo "PROJECT_ROOT=$DIR"
    break
  fi
  DIR="$(dirname "$DIR")"
done
```

If `.claude/` is not found, stop and tell the user:

```text
Could not find .claude/ directory. Run this command from within your project.
```

## Step 3: Resolve Source

**If `--source` is a local directory path:**

```bash
if [ ! -d "$SOURCE" ]; then
  # stop with error: "Source directory not found: $SOURCE"
fi
SOURCE_DIR="$(cd "$SOURCE" && pwd)"
SOURCE_COMMIT="$(git -C "$SOURCE_DIR" rev-parse HEAD 2>/dev/null || date +%s)"
```

**Otherwise, clone from remote:**

```bash
TEMP_DIR="$(mktemp -d)"
git clone --depth 1 "$SOURCE" "$TEMP_DIR"
SOURCE_DIR="$TEMP_DIR"
SOURCE_COMMIT="$(git -C "$SOURCE_DIR" rev-parse HEAD)"
```

If clone fails, stop and report the error.

## Step 4: Version Check

Read `$PROJECT_ROOT/.claude/.tooling-version` (if it exists) and compare the stored `commit` value against `$SOURCE_COMMIT`.

- If commits match and `--force` is NOT set: print "Already up to date (commit {short_hash}). Use --force to update anyway." and stop.
- If commits differ or `--force` is set: continue.
- If `.tooling-version` does not exist: continue (first update).

## Step 5: Discover Managed Files

*[truncated — see source for full prompt]*