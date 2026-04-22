# Ui

> !!! warning "Deprecated"
    **This component has been superseded by [MoltlerHub](moltlerhub/index.md).**
    
    MoltlerHub provides a richer experi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Moltler Skills Manager UI

!!! warning "Deprecated"
    **This component has been superseded by [MoltlerHub](moltlerhub/index.md).**
    
    MoltlerHub provides a richer experience for browsing, discovering, and installing skills. 
    The Skills Manager UI (`moltler-ui`) is kept for local development but is no longer recommended for end users.
    
    **Use MoltlerHub instead**: `cd moltler-hub && npm run dev`

---

A local React-based web interface for managing elastic-script skills, procedures, and functions.

## Overview

The Skills Manager provides:
- **Browse** skills, procedures, and functions
- **View** implementation code and auto-generated documentation
- **Edit** with Monaco editor (VS Code-like experience)
- **Execute** skills directly from the UI

## Starting the UI

```bash
# As part of the full stack
./scripts/quick-start.sh --moltler

# Or standalone
cd moltler-ui
npm install
npm run dev
```

Access at: http://localhost:3000

## Features

### Tabbed Navigation

The UI organizes items into three tabs:
- **Skills** - AI-ready skills with MCP metadata
- **Procedures** - Reusable code blocks
- **Functions** - User-defined functions

### Skill Detail View

Click any item to open the detail flyout:

#### Implementation Tab
- Full source code in Monaco editor (read-only)
- Syntax highlighting for elastic-script
- Copy to clipboard

#### Documentation Tab
- Auto-generated markdown documentation
- Parameter tables
- Usage examples
- Rendered with proper formatting

### Editor

Create or edit items with:
- **Monaco Editor** - Full VS Code editing experience
- **Syntax Highlighting** - elastic-script keywords
- **Auto-completion** - Built-in functions and keywords
- **Code Templates** - Boilerplate for new items

### Execution

The **Invoke** button:
- Detects the item type from the code
- Generates appropriate CALL statement
- Executes and displays results
- Shows errors with helpful formatting

## Configuration

### Environment Variables

Create `.env.loc

*[truncated — see source for full prompt]*