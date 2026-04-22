# Command Reference

> This document provides a comprehensive reference for all Docu slash commands and their usage.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Command Reference

This document provides a comprehensive reference for all Docu slash commands and their usage.

## Command Syntax

All Docu commands follow this pattern:
```
@docu /command [arguments] [--options]
```

- **@docu** - Required prefix to invoke Docu chat participant
- **/command** - The command name (required)
- **[arguments]** - Positional arguments (varies by command)
- **[--options]** - Named options with values (optional)

## Document Creation Commands

### /new

Creates a new document with optional template and path specification.

#### Syntax
```bash
@docu /new "Document Title" [--template template-name] [--path directory/]
```

#### Parameters
- **Document Title** (required) - The title of the document to create
- **--template** (optional) - Template to use for document creation
- **--path** (optional) - Directory path where document should be created

#### Examples
```bash
# Create basic document
@docu /new "Getting Started Guide"

# Create with specific template
@docu /new "API Documentation" --template basic

# Create in specific directory
@docu /new "User Manual" --path docs/user-guides/

# Create with template and path
@docu /new "Product Requirements" --template prd --path specs/
```

#### Behavior
- Creates markdown file with kebab-case filename
- Applies specified template or uses basic template
- Creates directory structure if it doesn't exist
- Opens created file in VS Code editor
- Generates clickable file link in chat response

## Agent Management Commands

### /agent list

Lists all available agents with their descriptions and current status.

#### Syntax
```bash
@docu /agent list
```

#### Examples
```bash
@docu /agent list
```

#### Output
```
Available Agents:

🎯 PRD Creator (prd-creator)
   Phase: PRD | Status: Available
   Description: Product concept exploration and PRD generation

💡 Brainstormer (brainstormer)
   Phase: PRD | Status: Available
   Description: Ideation and concept expansion based on PRD context

📋 Requir

*[truncated — see source for full prompt]*