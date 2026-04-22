# Aliases

> Aliases in CycoD allow you to save frequently used command configurations as shortcuts, making it easier to reuse complex or common configurations without having to type them out each time.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Creating Aliases

Aliases in CycoD allow you to save frequently used command configurations as shortcuts, making it easier to reuse complex or common configurations without having to type them out each time.

## How Aliases Work

Aliases are stored as plain text files in an `aliases` directory within the CycoD configuration folders. Aliases can be stored in three different scopes:

1. **Local scope** - stored in the `.cycod/aliases` directory of the current working directory
2. **User scope** - stored in the user's CycoD configuration directory (`~/.cycod/aliases` on Unix, `%USERPROFILE%\.cycod\aliases` on Windows)
3. **Global scope** - stored in the system-wide CycoD configuration directory

When looking for an alias, CycoD searches in the local scope first, then the user scope, and finally the global scope.

## Creating an Alias

There are two different ways to create aliases, each with different use cases:

### 1. Using the `--save-alias` Option (Validated Aliases)

To create a validated alias that must be syntactically correct at creation time, use one of the following options followed by a name for your alias:

- `--save-alias` or `--save-local-alias` - Save in the local scope (current directory)
- `--save-user-alias` - Save in the user scope (available to the current user in any directory)
- `--save-global-alias` - Save in the global scope (available to all users)

Example:

```bash
cycod --system-prompt "You are an expert Python programmer who gives concise code examples." --save-alias python-helper
```

This will save all the command line options (except the save-alias option itself) to an alias named `python-helper` in the local scope.

To save an alias in the user scope:

```bash
cycod --system-prompt "You are an expert Python programmer who gives concise code examples." --save-user-alias python-helper
```

### 2. Using the `alias add` Command (Raw Aliases)

To create a raw alias that doesn't require syntax validation at creation time, use the `alias add

*[truncated — see source for full prompt]*