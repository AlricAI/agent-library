# Configuration Features

> This document explains the differences and relationships between various configuration features in CycoD: aliases, custom prompts, config files, and profiles.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Configuration Features in CycoD

This document explains the differences and relationships between various configuration features in CycoD: aliases, custom prompts, config files, and profiles.

## Overview

CycoD offers multiple ways to configure and customize your experience:

- **Aliases**: Command-line shortcuts for launching CycoD with specific parameters
- **Custom Prompts**: Text templates used within a chat session
- **Config Files**: Persistent application settings
- **Profiles**: Collections of settings that can be loaded as a unit

All these features use a common scoping system with three levels:
- **Local**: Specific to the current directory
- **User**: Specific to the current user
- **Global**: Available to all users system-wide

## Aliases

Aliases are shortcuts for frequently used command-line options.

### Key Characteristics

- **Purpose**: Allow users to save a set of command-line parameters under a name for easy reuse
- **Usage**: Called with `--aliasname` from the command line
- **Storage**: Stored as `.alias` files in `aliases` directories
- **Scopes**: Support local, user, and global scopes
- **Creation**: Created using `--save-alias`, `--save-user-alias`, or `--save-global-alias`
- **Management**: Managed with dedicated commands:
  - `cycod alias list` - Lists all aliases
  - `cycod alias get` - Views a specific alias
  - `cycod alias delete` - Deletes an alias
- **Content**: Contains command-line arguments that would otherwise be typed manually

### Example

```bash
# Create an alias
cycod --system-prompt "You are an expert in Python programming." --save-alias python-expert

# Use the alias
cycod --python-expert --input "Write a function to sort a list"
```

## Custom Prompts

Prompts are reusable text templates that can be quickly inserted into chat conversations.

### Key Characteristics

- **Purpose**: Provide quick access to frequently used text templates during chat sessions
- **Usage**: Called with `/promptname` during a chat session
- 

*[truncated — see source for full prompt]*