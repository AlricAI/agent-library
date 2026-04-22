# Templates

> CycoD provides a powerful templating system that allows you to create dynamic content with variables, conditionals, and expressions.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Templates

CycoD provides a powerful templating system that allows you to create dynamic content with variables, conditionals, and expressions. This document explains how to use templates effectively in your interactions with the AI.

## Overview

Templates in CycoD allow you to:

1. Insert variables into text
2. Use conditional statements to include or exclude sections
3. Perform calculations and evaluations in-line
4. Process environment variables dynamically

## Variable Substitution

The simplest use of templates is variable substitution, which allows you to insert the value of a variable into text.

### Basic Syntax

```
Hello, {name}!
```

If the variable `name` has the value "John", this would output:

```
Hello, John!
```

### Variable Sources

Variables can come from:

1. Command line arguments (using `--var NAME=VALUE` or `--vars NAME1=VALUE1 NAME2=VALUE2 ...`)
2. Foreach loop variables (using `--foreach var NAME in VALUES...`)
3. Environment variables
4. Special built-in variables
5. Variables set within templates

### Special Variables

The following special variables are available:

| Variable | Description |
|----------|-------------|
| `os` | Operating system string |
| `osname` | Operating system platform name |
| `osversion` | Operating system version |
| `date` | Current date (YYYY-MM-DD format) |
| `time` | Current time (HH:MM:SS format) |
| `datetime` | Current date and time |
| `year` | Current year |
| `month` | Current month |
| `day` | Current day |
| `hour` | Current hour |
| `minute` | Current minute |
| `second` | Current second |
| `random` | Random number between 0 and 999 |

## Conditionals

Templates support conditional statements to include or exclude sections based on conditions.

### Basic Syntax

```
{{if condition}}
  Content to include if condition is true
{{else}}
  Content to include if condition is false
{{endif}}
```

### Multiple Conditions

```
{{if condition1}}
  Content for condition1
{{else if condition2}}
  Content fo

*[truncated — see source for full prompt]*