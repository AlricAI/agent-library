# Tool Registry Patterns

> > Separate what tools exist from how to invoke them.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tool Registry Patterns

> Separate what tools exist from how to invoke them. Register once, filter anywhere.

## The Problem

As tool counts grow, you hit three problems:

1. **Coupling**: Tool lists are hard-coded in prompts or configs. Adding a tool means touching multiple files.
2. **Testing**: You can't test routing logic without invoking real tools.
3. **Trust boundaries**: You want different tool sets in different contexts (read-only audit mode vs. full execution mode) without duplicating code.

## The Pattern

Maintain a **tool registry** — a central map of name → metadata. Load it once at startup. Filter it per context. Pass only the allowed subset to the model.

### Tool Entry Schema

```json
{
  "name": "write_file",
  "description": "Write content to a file on disk",
  "category": "filesystem",
  "source": "mcp:filesystem",
  "destructive": true,
  "requires_confirmation": false
}
```

The registry stores metadata, not implementations. Implementations live elsewhere and are looked up by name at execution time.

### Registry Snapshot (JSON)

Capture the registry to a file. This snapshot becomes a stable reference surface for testing, auditing, and documentation generation.

```json
{
  "version": "1.0.0",
  "captured_at": "2026-03-31T10:00:00Z",
  "tools": [
    { "name": "read_file", "category": "filesystem", "destructive": false },
    { "name": "write_file", "category": "filesystem", "destructive": true },
    { "name": "run_bash", "category": "shell", "destructive": true },
    { "name": "search_web", "category": "external", "destructive": false }
  ]
}
```

Commit this snapshot. Diffs make tool additions/removals visible in PRs.

### Loading and Filtering

```python
class ToolRegistry:
    def __init__(self, snapshot_path: str):
        with open(snapshot_path) as f:
            data = json.load(f)
        self._tools = {t["name"]: t for t in data["tools"]}

    def get(self, name: str) -> dict | None:
        return self._tools.get(name.lower())

 

*[truncated — see source for full prompt]*