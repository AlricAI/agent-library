# ISSUES

> ## Overview

The Issues system provides structured representation of code problems found by agents. Each issue contains:

- **File location** - which 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Issues System

## Overview

The Issues system provides structured representation of code problems found by agents. Each issue contains:

- **File location** - which file has the issue
- **Line range** - start and end line numbers
- **Severity** - critical, high, medium, or low
- **Category** - security, performance, bug, quality, style, or docs
- **Descriptions** - short and full descriptions
- **Suggestion** - how to fix the issue
- **Agent info** - which agent found it
- **Rule info** - which rule(s) triggered it
- **Evidence** - concrete code proof
- **Confidence** - certainty level 0-100

## Issue Structure

```typescript
interface Issue {
  file: string;              // File path (e.g., "src/example.ts")
  lineStart: number;         // Starting line number
  lineEnd: number;           // Ending line number
  severity: IssueSeverity;   // "critical" | "high" | "medium" | "low"
  category: IssueCategory;   // "security" | "performance" | "bug" | "quality" | "style" | "docs"
  shortDescription: string;  // Brief one-line description
  fullDescription: string;   // Detailed explanation
  suggestion?: string;       // How to fix it (optional)
  agent: string;             // Agent name that found the issue
  rule?: string;             // Rule(s) that triggered this issue (optional)
  evidence?: string;         // Concrete code proof that demonstrates the issue (optional)
  confidence?: number;       // Certainty level 0-100 (optional)
}
```

## Severity Levels

| Severity | Icon | Color | Description |
|----------|------|-------|-------------|
| `critical` | ✗ | Red | Critical issues that must be fixed immediately |
| `high` | ⚠ | Yellow | Important issues that should be addressed soon |
| `medium` | ○ | Blue | Moderate issues worth reviewing |
| `low` | ◇ | Cyan | Minor issues or suggestions |

## Categories

| Category | Icon | Description |
|----------|------|-------------|
| `security` | 🔒 | Security vulnerabilities and risks |
| `performance` | ⚡ | Performanc

*[truncated — see source for full prompt]*